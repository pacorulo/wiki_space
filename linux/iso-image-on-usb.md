It is really simple. Go to a Terminal and type:
```
    sudo dd if=~/Desktop/linuxmint.iso of=/dev/sdx oflag=direct  bs=1048576
```
Where _~/Desktop/linuxmint.iso_ is the name and location of your downloaded image (located at the desktop in this example) and _/dev/sdx_ is the target USB drive. If your system doesn't support _oflag=direct_, you can just leave it out as it is simply intended to speed up the process a bit.

If you don't know about the target USB drive path, run this command and figure out your destination drive.
```
    sudo fdisk -l
```
Warning: Make sure to set the correct device path, as this process will delete all data that was on the specified device previously!

Remember, don't include an integer for the USB drive, e.g. _/dev/sdx1_, as it would refer to the existing partition on that drive and not the drive itself.

When the USB has been properly created by _dd_, there should be an output similar to this:
```    
    sudo dd if=~/Desktop/linuxmint.iso of=/dev/sdb oflag=direct bs=1048576
    706+1 records in
    706+1 records out
    740601856 bytes (741 MB) copied, 91.7024 s, 8.1 MB/s
```
