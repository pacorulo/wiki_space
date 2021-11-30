Lista sólo los subdirectorios del directorio /usr (la línea empieza con "d"):
```
   ls -l /usr | grep '^d'
```
Lista sólo los archivos que otros pueden leer y escribir en el directorio principal:
``` 
  ls -l / | grep '.......rw'
```
Busca usuarios sin contraseña; caracteres al principio de línea que no sean ":", y luego "::" (el segundo lugar, que es el de la contraseña, está vacío):
``` 
  grep '^[^:]*::' /etc/passwd
```
Busca usuarios que no pueden entrar al sistema; tienen un * en el lugar de la contraseña; \ escapa el significado del segundo *, que vale como caracter a buscar:
``` 
  grep '^[^:]*:\*:' /etc/passwd
```
Con el comando citado conseguiremos pasar al fichero2 las líneas que contengan caracteres del fichero 1, o lo que es lo mismo, pasar todo excepto las líneas en blanco. Opción interesante si no nos manejamos con comandos como sed, awk, etc.:
```
  grep . fichero > fichero2
```
Busca cadenas comenzadas opcionalmente por un dígito y los caracteres ab, todo el paréntesis 0 o más veces, y hasta encontrar la cadena 1234:
```
  egrep "([0-9]+ab)*1234" archivo
```
