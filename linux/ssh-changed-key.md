We get:
```
$ ssh user@10.10.10.10
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
7f:4e:c6:73:55:1f:ac:b9:33:16:7a:3a:c2:a0:60:3f.
Please contact your system administrator.
Add correct host key in /home/NAMEPC/.ssh/known_hosts to get rid of this message.
Offending key in /home/NAMEPC/.ssh/known_hosts:1
RSA host key for 10.10.10.10 has changed and you have requested strict checking.
Host key verification failed.
```

Then we just have to remove the entry from known_hosts:
```
$ cd /home/user/.ssh
$ cp known_hosts known_hosts-old
$ sudo vi known_hosts
```
Now we have just to connect and accept the new key.

