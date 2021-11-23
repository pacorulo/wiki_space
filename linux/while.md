Delete all processes:
```
while read cont; do echo $cont; docker rm -f $cont; done < <(docker ps -a| awk '!/^CONT/{print $1}')
```

