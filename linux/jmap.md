From man page:
```
	jmap - Prints shared object memory maps or heap memory details for a process, core file, or remote debug server. This command is experimental and unsupported.
```
The jmap command prints shared object memory maps or heap memory details of a specified process, core file, or remote debug server. If the specified process is running on a 64-bit Java Virtual Machine (JVM), then you might need to specify the -J-d64 option, for example: 
```
	jmap-J-d64 -heap pid
```
