If you want to know which process is using a file:
```
fuser path-to-file/file.log
```
(firt you obtain the pid process is using the file)

```
ps -p `fuser path-to-file/file.log`
```	
(finally with "ps- p" we obtain the information about the pid and process name).
