# raspberry pi 

## gertboard

software https://github.com/ChrisCummins/gertboard_sw/tree/master

| local file |reference    | notes   |
|:------------------------|:------------------------|:------------------------|
| gertboard c software github |  https://github.com/ChrisCummins/gertboard_sw/tree/master   |  |
| [assembled_gertboard_schematics.pdf](../assembledassembled_gertboard_schematics.pdf)  | [assembled_gertboard_schematics - reference](https://www.openhacks.com/uploadsproductos/assembled_gertboard_schematics.pdf) |    |
|                        |                          |           |
|                        |                          |           |
|                        |                          |           |
|                        |                          |           |
|                        |                          |           |
|                        |                          |           |


## WiringPi

[WiringPi](https://github.com/WiringPi/WiringPi) is a library which can easily control the output pins of a Raspberry PI GPIO. 

To install wiring pi, you need do download the latest 32 bit package from the github [WiringPi releases](https://github.com/WiringPi/WiringPi/releases) site and install it on your local pi.

You can download the package into your Pi using `wget` which is a command line based browser.

```
wget https://github.com/WiringPi/WiringPi/releases/download/3.10/wiringpi_3.10_armhf.deb
sudo apt-get install ./wiringpi_3.10_armhf.deb 

```
WiringPi provides a command `gpio` which can control the pins from the command line.

```
gpio -h       # provides a simple list of commands
man gpio      # provides a full set of instructions
gpio readall  # lists the state of all of the pins
```
## setting up the GertBoard



## pin out details pi

GPIO - General Purpose Input/Output, aka "BCM" or "Broadcom".

https://pinout.xyz/ gpio pin layouts pi

BCM / Broadacom == GPIO pins are the pins on hte broadcom device

Wiring pi - attempt to standardise wiring - WiringPi uses its own pin numbering scheme, this page illustrates how WiringPi numbers your GPIO pins
