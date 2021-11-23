If we want for format the date in the way _date +%X_:
```
    +"%A" - Get weekday in full format i.e. as Tuesday
    +"%a" - Get weekday in abbreviated format i.e. as Tue
    +"%u" - Get day of week starting with Monday (1), i.e. mtwtfss
    +"%w" - Get day of week starting with Sunday (0), i.e. smtwtfs
```
Format current date:
```
_now=`/usr/local/bin/date +'%d/%m/%Y %H:%M:%S'`
```
Get day of the week as number:
```
date +%u
```
will be 1 on Monday,...


# 

Check if two remote nodes are syncrhonized:
```
ntpdate ip_maq_remota
```
```
ntpq -p
remote           refid      			st 	t 	when poll reach   delay   offset disp
================================================================================
*192.168.1.131   192.168.4.42     3 	u   21   64  	377     0.70    -0.155 0.15
```
