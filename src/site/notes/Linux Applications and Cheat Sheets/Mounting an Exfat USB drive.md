---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/mounting-an-exfat-usb-drive/"}
---


FAT/FAT32/exFAT filesystems do not support users per file as common Linux filesystems, AFAIK. So, `chown` and `chgrp` will not work. However you can specify a single user/group for all files during mount

```
sudo mount /dev/sdc /mnt/media/ -o uid=1000,gid=1000
```

The group does not have write permissions. To change that add `umask=002` to the options in your fstab-line:

```
UUID=XXXX-XXX /media/my-drive exfat defaults,uid=1000,gid=1002,umask=0002 0 0
```
The above invocation is for mounting a USB drive into a Samba share.

more about [[[umask\|[umask]] ]([permissions - "dmask" and "fmask" mount options - Ask Ubuntu](https://askubuntu.com/questions/429848/dmask-and-fmask-mount-options/429858#429858))here.