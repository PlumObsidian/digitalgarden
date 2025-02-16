---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/raspberry-pi/saving-default-alsa-settings-bodge/","tags":["linux","audio","alsa","howto","raspberrypi"]}
---

Set volume in alsamixer to desired level of neighbour bothering.

```bash
sudo alsactl --file ~/.config/asound.state store
```

You may need to make a .config first in shell

```bash
sudo alsactl --file ~/.config/asound.state store
```


```
sudo nano ~/.bashrc
```

append the bottom of the file..

```bash
 fi
fi
alsactl --file ~/.config/asound.state restore
```

Reboot and 
plug your ears.