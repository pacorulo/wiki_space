Mount the temporary folders into RAM

If we have enough RAM we can move into it the temporary folders of the system to aleviate the disk (these are folders written by out apps, that are removed once we poweroff the pc):
    
```
sudo gedit /etc/fstab
```

and paste this two lines:
```
    tmpfs /tmp tmpfs noatime,nodiratime,nodev,nosuid,mode=1777,defaults 0 0

    tmpfs /var/tmp tmpfs noatime,nodiratime,nodev,nosuid,mode=1777,defaults 0 0
```
