# Declinometer Software Setup

Configuring a new SOLAR-360 for threepio. Assumes wiring is correct — see
[interface.md](interface.md) for pinout and DB9 wiring.

## Prerequisites

Threepio must **not** be running. The serial port is exclusive to one process.

```bash
uv run python -m _tools.dec_probe            # auto-detects FTDI VID:PID=0403:6001
uv run python -m _tools.dec_probe /dev/cu.usbserial-XXXX   # or name it explicitly
```

Auto-detection matches the FTDI adapter's USB ID. A built-in COM port has none —
pass the port explicitly, or set `THREEPIO_DEC_PORT`.

## 1. Probe first

```bash
uv run python -m _tools.dec_probe --quick --out data/probe_<serial>.log
```

Read the `DIAGNOSIS` line at the bottom. Everything below is only needed if it
isn't already correct.

## 2. What threepio requires

| Setting | Required value | Why |
| --- | --- | --- |
| Baud / framing | **38400 8N1** | hardcoded in `_tools/minitars.py` |
| Protocol | LD serial (not NMEA) | `_parse` reads the LD format |
| Output format | **ASCII** `+xxx.xxx\r` | binary frames get discarded |
| Output mode | **continuous** | `handshake()` requires streaming |
| Interval | **100 ms (10 Hz)** | factory default is 1000 ms — works, but 10x slow |

## 3. Configure a factory-fresh unit

Commands are **lower case, exactly 7 bytes**, written in a single call — the
sensor discards a command with >100 ms between characters. All settings persist
to non-volatile memory.

```python
import time, serial

with serial.Serial("/dev/cu.usbserial-XXXX", baudrate=38400, timeout=1.0,
                   rtscts=False, dsrdtr=False, xonxoff=False) as ser:
    for cmd in (b"setoasc", b"str0100", b"setcasc"):
        ser.reset_input_buffer()
        ser.write(cmd)          # one write; never byte-by-byte
        ser.flush()
        time.sleep(0.3)
        print(cmd, "->", ser.read(ser.in_waiting or 0))
```

Order matters: `setoasc` and `str0100` before `setcasc`, so the stream starts in
the right format and at the right rate.

## 4. Command reference

| Command | Effect | Reply |
| --- | --- | --- |
| `gettemp` | temperature | `+22.8\r` ASCII, or 2-byte INT16 / 100 in binary |
| `get-360` | angle | `+090.448\r` ASCII, or 4-byte big-endian INT32 / 1000 |
| `setoasc` | output -> ASCII | `OK` |
| `str0100` | continuous interval -> 100 ms (10 Hz); range `0050`-`9999` | `OK` |
| `setcasc` | start continuous ASCII | `OK` (some units stay silent — harmless) |

Unverified but documented, if the probe reports NMEA mode:
`$PLDL100,1*38\r\n` returns the unit to the LD protocol.

**Not** the low-pass filter. That is a separate setting (0.125–16 Hz damping),
and the datasheet states it *"does not relate to output data rate."* Don't chase
it for rate problems.

## 5. Verify

```bash
uv run python -m _tools.dec_probe --quick
```

Expect:

```
  38400   8N1        9B ld-ascii          6B ld-temp <<<
=== output rate === 60 angle frames in 6.0s = 10.00 Hz  (malformed 0)
DIAGNOSIS: MISCONFIGURED, NOT BROKEN — ... (ld-ascii format, continuous/interval mode)
```

Then start threepio. A good log looks like:

```
INFO MiniTars: opened ... baudrate=38400 bytesize=8 parity=N stopbits=1
INFO handshake: already streaming ASCII angles
```

## 6. Quick triage

| Symptom in probe output | Cause | Fix |
| --- | --- | --- |
| `ld-binary` / `ld-binary-temp` | binary output mode | `setoasc` |
| Valid reply, `passive` column silent | poll mode | `setcasc` |
| Rate < 5 Hz | `str1000` default | `str0100` |
| `nmea` | NMEA protocol | `$PLDL100,1*38\r\n` |
| Valid reply at a rate other than 38400 | non-standard baud | reconfigure unit or software |
| Reply same length as command sent | our own Txd echoing back — not a reply | wiring |
| Silent at all baud x framing | not transmitting | hardware, not software |

`--write` is off by default so the probe never rewrites a unit's NVM during
diagnosis. `setoasc` / `setcasc` are only sent when you pass it.

## Notes

Two units of the same part number can behave completely differently out of the
box, because format, mode, interval and baud all live in NVM. A factory-fresh
unit ships in **binary, poll mode, 1000 ms** — none of which threepio accepts,
and none of which indicate a fault. Probe before suspecting hardware.
