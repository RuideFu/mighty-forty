## **8/10/26**
### Caiden

```python
# Do to lack of microHDMI adapters, the rpi 5 has to be setup headless
# The pi was formatted for SSH, the login command and password are located in the vault
# The pi was setup for VNC and had its connection tested using Caiden's computer to get limited visual setup for formatting the rpi

$ sudo raspi-config
     -> Interface Options -> VNC -> Yes
```

## **8/11/26** 
### Caiden

```python
# Ran the following lines in terminal

# To install uv as needed for the threepio program
$ curl -LsSf https://astral.sh/uv/install.sh | sh
# No issues on this front

# Then cloned threepio for GitHub
$ git clone [https://github.com/finnjames/threepio.git](https://github.com/RuideFu/threepio)

# entered threepio and ran uv sync
$ cd threepio
$ uv sync
# No issues here again, all files seem in order
```

```python
# Installed VS Code for troubleshooting purposes
$ Sudo apt update
$ Sudo apt install code

# Start vs code by simply typing 'code' into terminal
```

```python
# Installed VS Code for troubleshooting purposes
$ Sudo apt update
$ Sudo apt install code

# Start vs code by simply typing 'code' into terminal
```
