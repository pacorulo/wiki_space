To check the size of the files of the current folder:
``` 
du -ks *|sort -nr
```
where:
```
du -s: muestra el espacio ocupado en el directorio actual.
du -s *: muestra los espacios ocupados por los subdirectorios del actual.
du -k: muestra los espacios ocupados por los subdirectorios del actual en Kbytes.
```

Ex.:
```
du -kx .|sort -k1n


du -h --max-depth=2 | sort -nr | grep G
```
