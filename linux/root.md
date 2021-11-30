To activate/deactivate root:
```
sudo passwd -l root --lock
sudo passwd -u root --unlock
```

Use the usermod command to add the user to the wheel group.
```
usermod -aG wheel username
```
By default, on CentOS, members of the wheel group have sudo privileges.
