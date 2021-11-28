Before:
```
    $ sudo lshw -C video
      *-display                 
           description: VGA compatible controller
           product: Skylake GT2 [HD Graphics 520]
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 07
           width: 64 bits
           clock: 33MHz
           capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:126 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:e000(size=64) memory:c0000-dffff
```
```
    $ man inxi
    $ inxi -G
    Graphics:  Device-1: Intel Skylake GT2 [HD Graphics 520] driver: i915 v: kernel 
               Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
               OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) v: 4.5 Mesa 19.0.8 
```
```
    $ grep modesetting /var/log/Xorg.0.log
    [     6.574] (==) Matched modesetting as autoconfigured driver 0
    [     6.574] (II) LoadModule: "modesetting"
    [     6.574] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
    [     6.574] (II) Module modesetting: vendor="X.Org Foundation"
    [     6.574] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
```

After:
```
    $ sudo apt-get remove xserver-xorg-video-intel
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages will be REMOVED:
      xserver-xorg-video-intel
    0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
    After this operation, 3.259 kB disk space will be freed.
    Do you want to continue? [Y/n] y
    (Reading database ... 345173 files and directories currently installed.)
    Removing xserver-xorg-video-intel (2:2.99.917+git20171229-1) ...
    Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
    Processing triggers for libc-bin (2.27-3ubuntu1) ...
```
```
    $ inxi -G
    Graphics:  Device-1: Intel Skylake GT2 [HD Graphics 520] driver: i915 v: kernel 
               Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
               OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) v: 4.5 Mesa 19.0.8 
```
```
    $ grep modesetting /var/log/Xorg.0.log
    [     6.574] (==) Matched modesetting as autoconfigured driver 0
    [     6.574] (II) LoadModule: "modesetting"
    [     6.574] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
    [     6.574] (II) Module modesetting: vendor="X.Org Foundation"
    [     6.574] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
```

It did not work and I had to reinstall the driver...



