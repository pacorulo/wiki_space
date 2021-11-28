That can clean out a lot of guff (old kernels, etc) that have been replaced. You can do a similar thing in Synaptic (load it up and select the status button and then the Auto-removeable option).
```
	$ sudo apt-get autoremove
	
	OR
	
	$ sudo apt-get autoremove --purge
```	
To delete downloaded packages (.deb) already installed (and no longer needed)
```
	$ sudo apt-get clean
```	
To remove all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repository or that have a newer version in the repository).
```
	$ sudo apt-get autoclean
```
To delete old kernel versions
```
	$ sudo apt-get remove --purge linux-image-X.X.XX-XX-generic
```
	If you don't know which kernel version to remove
```
	$ dpkg --get-selections | grep linux-image
```		
To delete all files from trash:
```
	$ rm -r ~/.local/share/Trash/info/ && rm -r ~/.local/share/Trash/files/
```

