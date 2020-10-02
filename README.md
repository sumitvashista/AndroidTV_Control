# AndroidTV Control
A bash script providing a bunch of functions to control your TV based on ADB.

This script provides a rich set of functions allowing to control your Android TV (and other Android based devices like the amazon Fire TV stick - may also work with other Android based device types) .

Basicly it uses ADB to send commands to the TV. In case of using it on a Raspberry Pi this means that you have to get and compile ADB for ARM. You also need to enable ADB connections on the TV in the settings menu (developer settings, e.g. FireTV) or running the appropirate java app. Check the Internet for more details. You should set the option to remember the pairing, otherwise you need to allow the connect each time you use the script. A new pairing is required any time you change the "calling device".
The target scenario is the integration with openHAB - a smart home gateway, but could also be integrated in any other scenario. I use it to switch on/off the TV, select channels, start NETFLIX etc.

You need to change the script code to reflect your IP setup:
tv_ip="192.168.xx.xx"       # IP address of the TV (device id 1)
tv_mac="xx:xx:xx:xx:xx:xx"  # MAC address of the TV (required to wake-on-lan"
fire_tv_ip="192.168.xx.xx"  # IP address of the Fire TV (device id 2)
The MAC address can be obtained from the TVs network settins/status

You could enable using cec-client (requires package cec-utils) to power TV using HDMI and also selecting the HDMI channel for the AVR (in this case you need also to set the hdmi_addr_avr var, see script comment).

NETFIX, TV Guide and Videotext are implemented by starting the appropirate App using ADB (thanks Paul for providing the information).

Depending on the TV model you may need to adjust the way the TV is powered on and off. My requires a sleep and not pressing the power button. This ensures that the TV is switched on when its OFF and switches off when its ON. Using the power button as a toggle will fail once you used the remote to do it manually and openHAB doesn't get informed on that.

Please note:
- The script reflects my scenario and doesn't have the target to be a universal implementation supporting all types of Android TVs. Is was tricky to get everything running, esp. the fact that the TV is accepting the ADB connection.
- I'm not a bash expert, so maybe some optimizations and more specific error handling could be supplied.

Looking forward to any contribution. I could also provide some scripts for waking up a Apple-TV or controlling the Telekom Entertain Receiver. If you are interested feel free to cantact me.

You could follow up the following thread in the openHAB community:
https://community.openhab.org/t/philips-android-tv/15267/25

HappySmartHoming & have fun,
Markus

Usage: androidtv_control.sh <command> [<device id>[log | trace | debug]]
Run without parameters or --help to get iformation on the usage, check the script for more command line options.

