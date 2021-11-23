Find all files with name like mc*.db and see how much disk it consumes and then sum up all that quantities in G for Gigabytes:
```
find . -name mc*.db -exec du -sh {} \; |  grep G | awk 'BEGIN { SUM = 0 } { SUM += $1 } END { print "La suma de Gigas en mc: " SUM }'
```
To find all the different extensions contained in a folder:
```
$ find . -type f -name "*.*" | awk -F. '{print $NF}' | sort -u
```	
To find all different folder names under a directory:
```
$ find . -type d | awk -F. '{print $NF}' | sort -u
```

La orden: __find / -name *.dbf__  no quita los nulos por lo que la salida es monstruosa, así que mejor la primera orden que aparece.

Realiza búsqueda desde el directorio en este caso raíz y todo lo que hay dentro de él bajo el parámetro de búsqueda incluido entre comillas dobles.
```
find . -name "*.file" -type f -print | xargs file | grep ASCII | cut -d: -f1
```
Y así ejecutamos un file sobre cada fichero encontrado y luego buscamos por un patrón para obtener finalmente los ficheros que cumplen ese patrón en la búsqueda que hemos ejecutado.
```
find + mtime:
```
```
find . -mtime ls -size +1000 -name * -ls
```
este comando busca ficheros en el dir. actual y subdir. con fecha de modificación desde hace 10 días antes y cn tamaño superios a 1000 bytes, para finalmente listar la salida.


Con este comando comprimimos con gzip los fichero que tienen fecha de modificación superior a 24 horas (es decir, ficheros que fueron modificados en fecha anterior al día de ayer):
```
find . -name * -mtime +0 -exec gzip -v {} \; ----esta no suele funcionar pero por si....----
find . -name "*" -mtime +0 -exec gzip -v {} \;
```

Borramos los ficheros de log que sean de más de 1 semana:
```
find . -name "*log*" -mtime +6 -exec rm {} \;
```

La sentencia que se debe ejecutar para borrar los ficheros con mas de dos días de antiguedad:
 ```
find . -type f -ctime +2 -exec rm {} \;
```

Listado de ficheros modificados en las últimas 24 horas
```
$ find . -mtime 0
```
Listado de ficheros modificados hace más de 24 horas
```
$ find . -mtime +0
```
Listado de fichero modificados entre hace 24 y 48 horas
```
$ find . -mtime 1
```
Listado de ficheros modificados en menos de 48 horas
```
$ find . -mtime -1
```
Listado de ficheros modificados hace más de 48 horas
```
$ find . -name +1
```

Ej.:
```
find /opt/sera/logs -name "sera.log.????-??-??" -mtime +10 -ls -exec gzip {} \;
```

Para sacar el último fichero actualizado en el dir. actual:
```
find . -newer .
```
Modificados en los últimos 40 minutos ---- OPCIÓN NO VÁLIDA EN TODA DISTRIBUCIÓN UNIX:
```
$ find . -mmin -40
```

#### find + exec:
1. find /opt/sera/adsl/logs -name "GestorAlarmasProactivas.log.????-??-??" -mtime +10 -ls -exec gzip {} \;
2. find /opt/sera/adsl/logs -name "sera.log.????-??-??" -mtime +10 -ls -exec gzip {} \;

Con la siguiente orden buscamos dentro del dir /users los archivos que sean mayores que 10 megas:
```
find /users -size +10240000c -exec ls -lrst {} \;
```
```
find . -name "C2011-0*" -mtime +20 -exec gzip -v {} \;
```
Con esta orden comprimimos todos los ficheros que cumplan el patrón en el dir. actual (en este caso /users/eoc//HcoDiscoBkp de M2OC1) y que verifiquen que tienen más de 20 días.

#### find + exec + mtime:
```
find . -name "core.socmv2.*" -mtime +7 -exec gzip -v {} \;
```

Para buscar una cadena de texto en los ficheros de un sistema:
```
grep -il "hello" `find .`
```

I find that another useful way of doing a recurvsive grep
```
find . -type f -exec grep -il "hello" {} \;
```
or if you know the file type
```
find . -type f -name "*.ext" -exec grep -il "hello" {} \
```
and/ or if you just want your files
```
find . -type f -user myname -name "*.ext" -exec grep -il "hello" {} \
```
and obviously you can still output this to a log file using the redirect > 

```
find /users/*/LOG_AGENTE -size +10240000c -exec ls -lrst {} \; 2> /dev/null | grep 'log$' | awk '{ print $10 }' > ~/salida.txt
```

To find symlinks in all subdirectories from the current directory:
```	
find . -type l
```

Find and move files to a target folder:
```
find . -type f -exec mv -t ../input/ {} +
```

To remove executable bit from all txt files under a directory (first we need to tell our shell the new line character is \n as if not it will fail with txt files containing spaces in their names and would cause major problems on some files):
```
$ export IFS=$'\n'
$ for i in `find ~/Documents/oposRelated -name '*.txt' -type f`; do chmod -x $i; done
```
