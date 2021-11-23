```
dstat - versatile tool for generating system resource statistics
```


To get all the default parameter but also memory usage:
```
ubuntu@ds210:~$ dstat -am
--total-cpu-usage-- -dsk/total- -net/total- ---paging-- ---system-- ------memory-usage-----
usr sys idl wai stl| read  writ| recv  send|  in   out | int   csw | used  free  buff  cach
 12   9  77   2   0|6740k 1313k|   0     0 |   0     0 |1480  4120 | 667M 4012M 72.4M 1060M
  2   1  98   0   0|   0    60k|   0   280B|   0     0 | 229   381 | 668M 4011M 72.4M 1060M
  4   1  95   0   0|   0     0 |   0     0 |   0     0 | 321   762 | 668M 4011M 72.4M 1060M
  4   1  96   0   0|   0     0 |   0     0 |   0     0 | 217   449 | 668M 4011M 72.4M 1060M
  4   1  96   0   0|   0     0 |   0     0 |   0     0 | 206   507 | 668M 4011M 72.4M 1060M
```
