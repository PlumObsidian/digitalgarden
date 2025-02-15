---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/raspberry-pi/wi-fi-raspberry-pi/","tags":["linux","raspberrypi","howto"]}
---

To scan for available WiFi networks on a Raspberry Pi using the command line, type "==sudo iwlist wlan0 scan==". 

Explanation:

- **sudo:** This keyword is used to execute the command with elevated privileges.
- **iwlist:** A command used to list information about wireless networks.
- **wlan0:** This refers to the default wireless interface on most Raspberry Pis. 

What the output shows:

- **SSID:** The network name.
- **Channel:** The frequency channel the network is using.
- **Signal strength:** How strong the signal is from the network.