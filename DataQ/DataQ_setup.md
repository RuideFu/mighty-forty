# **Setting Up the DataQ for Linux Distributions**

The DataQ is arguably one of the essential hardware components of the 40 ft system. It is an analog to digital converter which takes the flux signals coming from the telescope in two channels and converts them to a digital signal which can be used to determine source intensity. Without the flux, we would not be able to make images and would only be able to rely on the strip chart to identify sources. 

## **Wiring**

The DataQ is fairly simple to set up, you need to wire the signal and ground into the source channels on the instrument. The threepio software looks for data coming from the first two source channels, so those should be the ports you use. The flux from the telescope is delivered by two coaxial cables, which you will need to both mount ports onto the side of your container *and* solder wires to the back of the ports to actually deliver a signal to the DataQ. 

The specifications document can be found in this folder, which contains much greater detail of how the device works and the dimensions of the device. 

## **Setting Up for RpiOS and USB Mode**

Setup instructions can be found in '
