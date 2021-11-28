If GRUB disappears we need a live CD and once we have again a Linux system we open a Terminal and do the same:

- check what's the name of my disks with:
	```	
	$ sudo fdisk -l
	[sudo] contraseña para pakete: 
	Disco /dev/sda: 119,2 GiB, 128035676160 bytes, 250069680 sectores
	Unidades: sectores de 1 * 512 = 512 bytes
	Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
	Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes
	Tipo de etiqueta de disco: dos
	Identificador del disco: 0xfe0ef564

	Dispositivo Inicio  Comienzo     Final  Sectores Tamaño Id Tipo
	/dev/sda1               2048 147204095 147202048  70,2G  7 HPFS/NTFS/exFAT
	/dev/sda2          147206142 250068991 102862850  49,1G  5 Extendida
	/dev/sda5          147206144 250068991 102862848  49,1G 83 Linux
	```

	Now I know I have a two (first one for Windows and the second for Linux)

- Therefore, we are going to use /dev/sda as our drive to install GRUB with the following commands:
	```
	sudo mount --bind /dev /mnt/ubuntu/dev &&
	sudo mount --bind /dev/pts /mnt/ubuntu/dev/pts &&
	sudo mount --bind /proc /mnt/ubuntu/proc &&
	sudo mount --bind /sys /mnt/ubuntu/sys
		
	sudo chroot /mnt/ubuntu

	grub-install /dev/sda

	grub-install --recheck /dev/sda

	update-grub

	exit &&
	
	sudo umount /mnt/ubuntu/sys &&
	sudo umount /mnt/ubuntu/proc &&
	sudo umount /mnt/ubuntu/dev/pts &&
	sudo umount /mnt/ubuntu/dev &&
	sudo umount /mnt/ubuntu
	```
- At that point we restarted the pc and now it starts up with Linux but not with grub (as only we recovered grub in Linux partition and still no Windows). Therefore, we nee to user boot-repair:
	```
	sudo boot-repair
	```
	> **Option 1**: it can, only by typing the previous command, resolve the problem, where the log files are under /var/log/boot-repair (and one more folder per date/execution)

	> **Option 2**: it can start showing some windows with some commands that must be executed manually in a parallel terminal, but once all commands are executed the GRUB is reinstalled on /dev/sda (on all drives, for all drives)

