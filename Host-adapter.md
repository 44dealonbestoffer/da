### Host adapter

The USB armory is primarily meant to be attached to a USB host, such as a
laptop or desktop computer. However, it can be also used as a standalone
computer by using a custom host adapter.

The host adapter leverages the fact that it is possible, by changing the Linux
kernel device tree configuration, to invert the role of the USB On-The-Go port
currently used as main plug for the board. This allows USB Armory to be used
independently as a host.

The host adapter needs to perform the following functions:

 * Bridging the USB Armory male plug to a USB Type A receptacle (gender changer).
 * Accepting power from a micro-USB input.

This simple conversion enables connection between the USB Armory, power supply,
and a USB device or hub. Therefore, it is only a matter of compiling the right
Linux kernel modules and the USB Armory can independently use a keyboard, USB
display, USB mass storage devices, USB WiFi dongle and more.

Connecting a powered USB hub to the adapter ensures that all the connected USB
devices have enough power to perform their tasks. Additionally, a micro-USB
cable we can power the USB Armory itself. Alternatively, a passive USB hub can
be used and a micro-USB charger (such as ones used for most mobile phones) can
provide power.

The host adapter can be easily built using a breadboard as follows (only
recommended for people with experience in DIY hardware and electronics):

  * D+, D- bridged from a Type A receptacle to the other
  * VBUS, GND shorted between the two Type A receptacles and a micro-USB one

Additionally the adapter is available for purchase along with the USB armory
board, please see information at the [USB armory project
page](http://inversepath.com/usbarmory).

![USB armory host adapter](https://www.crowdsupply.com/img/00e2/host-adapter-1_png_project-body.jpg)