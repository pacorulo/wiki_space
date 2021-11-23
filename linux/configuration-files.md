Para añadir repositorios (que son mirados por el update manager o synaptic):
```
    sudo vi /etc/apt/sources.list
```
Para poder utilizar root lo bloqueamos o desbloqueamos y le ponemos passwd una vez lo usamos por primera vez ya que en Mint usa inicialmente la del usr que tenemos:
```
    sudo passwd -l root --lock
    sudo passwd -u root --unlock
```
* passwd --comando a usar para cambiarla cuando seamos ese usr

Para modificar los directorios por defecto de nuestro home hay que modificar el fichero:
```
    /home/tu_usuario/.config/user-dirs.dirs
```
Para añadir el usuario al grupo de bluetooth:
```
    sudo usermod -aG bluetooth pakitori
```
Ver estado del servicio bluetooth:
```
    systemctl status bluetooth.service

    pactl load-module module-bluetooth-discover
```
>  (https://github.com/blueman-project/blueman/issues/165)
	Optional purge all bluetooth
	sudo apt-get purge pulseaudio-module-bluetooth bluetooth bluez-* bluez
	reinstall bluemon and pulseaudio module for bt
	sudo apt-get install blueman bluez pulseaudio-module-bluetooth
	Load missing module
	pactl load-module module-bluetooth-discover
	open bluemon applet and "set up new device", allow to pair.
	open bluemon aplplet >devices. in menue >devices, choose to connect to 'audio synce' and 'headset'. Im sure your setup 	may vary here.
	also within bluemon applet>devices: menue >devices>profile choose >profile A2DP (or what ever you want)


Instalar virtualbox

- bajar la última versión para ubuntu en 64 bits (para Mint 18 Sarah era la Ubuntu 16.04 ("Xenial")
- reinstalar dkms si kernel no funciona (virtualbox-host-dkms)

##### GESTION USUARIOS CENTOS:
```
    # adduser username

    Use the passwd command to update the new user's password.

    # passwd username
```
Set and confirm the new user's password at the prompt. A strong password is highly recommended!
```
    Set password prompts:
    Changing password for user username.
    New password:
    Retype new password:
    passwd: all authentication tokens updated successfully.
```
Use the usermod command to add the user to the wheel group.
```
    # usermod -aG wheel username
```
By default, on CentOS, members of the wheel group have sudo privileges.

