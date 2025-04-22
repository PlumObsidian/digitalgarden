---
{"dg-publish":true,"permalink":"/software/roon/roon-on-pi-zero-2-w/"}
---


I wanted a Roon endpoint on my little Pi Zero 2W but Ropiee won't pick up the WM8960 hat I have for it.

I had it running already as a Plexamp endpoint but wanted Roon for Tidal play.

The solution was to install Roonbridge with this script:


``` bash
sudo apt update && sudo apt upgrade -y wget https://download.roonlabs.net/builds/roonbridge-installer-linuxarmv8.sh chmod +x roonbridge-installer-linuxarmv8.sh sudo ./roonbridge-installer-linuxarmv8
```
To connect to the server I had to stop the Plexamp instance to free up the Alsa driver and set 'DSP for volume control but now works nicely..

Now in the garden hammock running this little thing on solar power 😉

Diagnostics like so..

pi@raspberrypi:~ $ systemctl status roonbridge
● roonbridge.service - RoonBridge
     Loaded: loaded (/etc/systemd/system/roonbridge.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-06-11 21:28:26 EDT; 23h ago
   Main PID: 567 (start.sh)
      Tasks: 30 (limit: 191)
        CPU: 4min 59.349s
     CGroup: /system.slice/roonbridge.service
             ├─567 /bin/sh /opt/RoonBridge/start.sh
             ├─571 RoonBridge --debug --gc=sgen --server RoonBridge.exe
             ├─584 RoonBridgeHelper --debug --gc=sgen --server RoonBridgeHelper.exe
             ├─590 /opt/RoonBridge/Bridge/processreaper 584
             └─595 RAATServer --debug --gc=sgen --server RAATServer.exe