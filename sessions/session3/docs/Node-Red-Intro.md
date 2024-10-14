[session3](../../session3/) | [Intro to Node Red](../docs/Node-Red-Intro.md)

# Introduction to Node Red

Node-RED is a visual, low-code programming tool developed by IBM that connects hardware devices, APIs, and online services together. 
It's designed for the Internet of Things (IoT) but can be used for other applications as well.
Node-RED is easily installed on a Raspberry Pi and it provides a way to easily manipulate GPIO pins. 

   ![alt text](../docs/images/NodeRED1.png "Figure NodeRED1.png")

## Installing Node RED
Follow the instructions to [Install Node Red on Raspberry Pi](https://nodered.org/docs/getting-started/raspberrypi)

This will show you how to run a script to install Node Red.

Accept the defaults for the configuration script.

Once installed, you can  start Node-RED with the command  `node-red-start`  or using the icon under   Menu / Programming / Node-RED

Then point your browser to http://localhost:1880 or http://{your_pi_ip-address}:1880

The installer offers the option to install the standard GPIO library. 

See [interacting-with-pi-gpio](https://nodered.org/docs/faq/interacting-with-pi-gpio#node-red-node-pi-gpiod)

## Tutorials on Node RED

To try turning on and off GPIO pins which you configured on the Gertboard, try the following tutorial

[GPIO Pins on Node Red on a Pi](https://projects.raspberrypi.org/en/projects/getting-started-with-node-red/0)
 
In this resource you will learn how to use Node-RED to communicate with the Raspberry Pi’s GPIO pins. You will create a Node-RED ‘flow’ to control LEDs.

See also the tutorial [getting started with node red on raspberry-pi](https://randomnerdtutorials.com/getting-started-node-red-raspberry-pi/)


