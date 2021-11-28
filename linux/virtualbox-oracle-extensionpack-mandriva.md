Firts download the package (obvious). Second you can add it as an extension:
- go to Preferences in VirtualBox and in Extensions add the package


Errors (you can see this error):
```
    Failed to install the Extension Pack /home/pakitori/Download/Oracle_VM_VirtualBox_Extension_Pack-4.0.4-70112.vbox-extpack.
    The installer failed with exit code 1: VBoxExtPackHelperApp: error: Unable to locate 'pkexec', 'gksu' or 'su+xterm'. Try perform the operation using VBoxManage running as root.
```

To solve this I used the console with VBoxManage:
```
    $ VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.0.4-70112.vbox-extpack 
```
with the exit:
```
    tension_Pack-4.0.4-70112.vbox-extpack 
    0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
    Successfully installed "Oracle VM VirtualBox Extension Pack".
```

