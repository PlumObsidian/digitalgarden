---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/ghostty/ghostty/","tags":["linux","ghostty","ssh"]}
---

A nice terminal but a few tweaks needed to work under Win11 and WSL

Firstly, powertools for win 11 will allow the pinning of app to the taskbar.

config usually needs a few tweaks:

```
nano .config/ghostty/config
```
something like that.

Now set a nice them and a fallback for x-term:

```
theme = catppuccin-frappe
command = TERM=xterm-256color /usr/bin/bash
```

If Ghostty chokes on ssh for a remote host then this:

```
nano .ssh/config
```

```
Host *

  SetEnv TERM=xterm-256color
```

