Para saber a qué grupo pertenece un usuario hay varias fórmulas:
* id 'username'
	```
	      $ id -u username
	```      
	(and we get the uid)
* groups 'username' 
	```
        $ grep username /etc/group
        username:x:64992:
	```

Adding a user to sudoers group in Debian, we need to execute the command (as root):
```
    # gpasswd -a username sudo
    Adding user to the group sudo
```
or with some user with sudo rights just use sudo command with this user.
(if you used a user, then used su to convert it to root and apply the change, then after logoff as root you need also to logoff that user)

Adding/Removing a user to some group (in this case tty):
```
    $ sudo adduser username tty
    [sudo] password for username:     
    Adding user `username' to group `tty' ...
    Adding user username to group tty
    Done.
```
```    
    $ sudo deluser username tty
    Removing user `username' from group `tty' ...
    Done.
```

