## COMANDOS LINUX
* **ls**
Descripción: =list. listar contenido de directorios.
Ejemplos: ls, ls -l, ls -fl, ls --color

* **cp**
Descripción: =copy. copiar ficheros/directorios.
Ejemplos:cp -rfp directorio /tmp, cp archivo archivo_nuevo

* **rm**
Descripción: =remove. borrar ficheros/directorios.
Ejemplos: rm -f fichero, rm -rf directorio, rm -i fichero

* **mkdir**
Descripción: =make dir. crear directorios.
Ejemplos: mkdir directorio

* **rmdir**
Descripción: =remove dir. borrar directorios, deben estar vacios.
Ejemplos: rmdir directorio

* **mv**
Descripción: =move. renombrar o mover ficheros/directorios.
Ejemplos: mv directorio directorio, mv fichero nuevo_nombre, mv fichero a_directorio

* **date**
Descripción: gestion de fecha de sistema, se puede ver y establecer.
Ejemplos: date, date 10091923 

* **history**
Descripción: muestra el historial de comandos introducidos por el usuario.
Ejemplos: history | more

* **more**
Descripción: muestra el contenido de un fichero con pausas cada 25 lineas.
Ejemplos: more fichero

* **grep**
Descripción: filtra los contenidos de un fichero.
Ejemplos:cat fichero | grep cadena

* **cat**
Descripción: muestra todo el contenido de un fichero sin pausa alguna.
Ejemplos: cat fichero

* **chmod**
Descripción: cambia los permisos de lectura/escritura/ejecucion de ficheros/directorios.
Ejemplos: chmod +r fichero, chmod +w directorio, chmod +rw directorio -R, chmod -r fichero

* **chown**
Descripción: =change owner. cambia los permisos de usuario:grupo de ficheros/directorios.
Ejemplos: chown root:root fichero, chown pello:usuarios directorio -R

* **tar**
Descripción: =Tape ARchiver. archivador de ficheros.
Ejemplos: tar cvf fichero.tar directorio , tar xvf fichero.tar, tar zcvf fichero.tgz directorio, tar zxvf fichero.tgz

* **gunzip**
Descripción: descompresor compatible con ZIP.
Ejemplos: gunzip fichero

* **rpm**
Descripción: gestor de paquetes de redhat. Para instalar o actualizar software de sistema.
Ejemplos: rpm -i paquete.rpm, rpm -qa programa, rpm --force paquete.rpm, rpm -q --info programa

* **mount**
Descripción: montar unidades de disco duro, diskette, cdrom.
Ejemplos: mount /dev/hda2 /mnt/lnx, mount /dev/hdb1 /mnt -t vfat

* **umount**
Descripción: desmontar unidades.
Ejemplos: umount /dev/hda2, umount /mnt/lnx

* **wget**
Descripción: programa para descargar ficheros por http o ftp.
Ejemplos: wget http://www.rediris.es/documento.pdf

* **lynx**
Descripción: navegador web con opciones de ftp, https.
Ejemplos: lynx www.ibercom.com, lynx --source http://www.ibercom.com/script.sh | sh

* **ftp**
Descripción: cliente FTP.
Ejemplos: ftp ftp.ibercom.com

* **whois**
Descripción: whois de dominios.
Ejemplos: whois ibercom.com

* **who**
Descripción: muestra los usuarios de sistema que han iniciado una sesion.
Ejemplos: who, w, who am i

* **mail**
Descripción: envio y lectura de correo electronico.
Ejemplos: mail pepe@ibercom.com < fichero, mail -v pepe@ibercom.com < fichero

* **sort**
Descripción: ordena el contenido de un fichero.
Ejemplos: cat /etc/numeros | sort, ls | sort

* **ln**
Descripción: =link. para crear enlaces, accesos directos.
Ejemplos: ln -s /directorio enlace

* **tail**
Descripción: muestra el final (10 lineas) de un fichero.
Ejemplos:tail -f /var/log/maillog, tail -100 /var/log/maillog | more

* **head**
Descripción: muestra la cabecera (10 lineas) de un fichero.
Ejemplos: head fichero, head -100 /var/log/maillog | more

* **file**
Descripción: nos dice de que tipo es un fichero.
Ejemplos: file fichero, file *


## Comandos de administracion

* **sysctl**
Descripción: Configurar los paràmetros del kernel en tiempo de ejuecución.
Ejemplos: sysctl -a

* **ulimit**
Descripción: muestra los limites del sistema (maximo de ficheros abiertos, etc..)
Ejemplos: ulimit

* **adduser**
Descripción: añadir usuario de sistema.
Ejemplos: adduser pepe, adduser -s /bin/false pepe


* **userdel**
Descripción: = eliminar usuario de sistema
Ejemplos: userdel pepe

* **usermod**
Descripción: = modificar usuario de sistema
Ejemplos: usermod -s /bin/bash pepe

* **df**
Descripción: = disk free. espacio en disco disponible. Muy util.
Ejemplos: df, df -h

* **uname**
Descripción: =unix name. Informacion sobre el tipo de unix en el que estamos, kernel, etc.
Ejemplos: uname, uname -a

* **netstat**
Descripción: la informacion sobre las conexiones de red activas.
Ejemplos: netstat, netstat -ln, netstat -l, netstat -a

* **ps**
Descripción: =proccess toda la informacion sobre procesos en ejecucion.
Ejemplos: ps, ps -axf, ps -A, ps -auxf

* **free**
Descripción: muestra el estado de la memoria RAM y el SWAP.
Ejemplos: free

* **ping**
Descripción: heramienta de red para comprobar entre otras cosas si llegamos a un host remoto.
Ejemplos: ping www.rediris.es

* **traceroute**
Descripción: herramienta de red que nos muestra el camino que se necesita para llegar a otra maquina.
Ejemplos: traceroute www.rediris.es

* **du**
Descripción: =disk use. uso de disco. Muestra el espacio que esta ocupado en disco.
Ejemplos: du *, du -sH /*, du -sH /etc

* **ifconfig**
Descripción: =interface config. configuracion de interfaces de red, modems, etc.
Ejemplos: ifconfig, ifconfig eth0 ip netmask 255.255.255.0

* **route**
Descripción: gestiona las rutas a otras redes.
Ejemplos: route, route -n

* **iptraf**
Descripción: muestra en una aplicacion de consola TODO el trafico de red IP, UDP, ICMP. 
Permite utilizar filtros, y es SUMAMENTE UTIL para diagnostico y depuracion de firewalls
Ejemplos: iptraf

* **tcpdump**
Descripción: vuelca el contenido del trafico de red.
Ejemplos: tcpdump, tcpdump -u

* **lsof**
Descripción: muestra los ficheros(librerias, conexiones) que utiliza cada proceso
Ejemplos: lsof, lsof -i, lsof | grep fichero

* **lsmod**
Descripción: Muestra los modulos de kernel que estan cargados.
Ejemplos: lsmod

* **modprobe**
Descripción: Trata de instalar un modulo, si lo encuentra lo instala pero de forma temporal.
Ejemplos: modprobe ip_tables, modprobe eepro100

* **rmmod**
Descripción: Elimina modulos del kernel que estan cargados
Ejemplos: rmmod <nombre de modulo>

* **sniffit**
Descripción: Sniffer o husmeador de todo el trafico de red. No suele venir instalado por defecto.
Ejemplos: sniffit -i


### COMBINACIONES UTILES

Los comandos son muy útiles, pero con el conocimiento básico del shell y sus comandos tenemos armas muy poderosas que muestran todo el potencial del interprete de comandos Unix. A continuación se muestran algunos ejemplos avanzados de comandos que se usan con cierta frecuencia.
```
comando | grep filtro
```
A la salida de cualquier comando le podemos aplicar grep para que solo nos muestre
la informacion que nos interesa.
```
mail pepe@ibercom.com < fichero.conf
```
Con esto nos enviamos rapidamente un fichero de sistema a nuestra cuenta.

```
mail -v testing@dominio.com
```
Con el parametro -v, al terminar de escribir (. enter), veremos la traza del correo hasta el servidor,
si es aceptado o no.

```
find / -name 'filtro' -print
```
Find es un buscador de ficheros muy potente y con muchos parametros, todos los que nos podamos
imaginar (tamaños, fechas, tipos de archivos, etc..)


Al hacer **more**:
```
/cadena : podemos hacer busqueda de cadena
```
f : adelante
b: volver arriba
v: iniciar vi en la linea que estamos

