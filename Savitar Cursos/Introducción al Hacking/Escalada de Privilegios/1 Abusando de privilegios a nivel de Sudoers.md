- Tags : #escalada #escalada_privilegios #sudo #escalada_privilegios_sudo

**Recursos**:  **GTFOBins**: [https://gtfobins.github.io/](https://gtfobins.github.io/)


El archivo **/etc/sudoers** es un archivo de configuración en sistemas Linux que se utiliza para controlar el acceso de los usuarios a las diferentes acciones que pueden realizar en el sistema. Este archivo contiene una lista de usuarios y grupos de usuarios que tienen permisos para realizar tareas de administración en el sistema.

El comando “**sudo**” permite a los usuarios ejecutar comandos como superusuario o como otro usuario con privilegios especiales. El archivo sudoers especifica qué usuarios pueden ejecutar qué comandos con sudo y con qué privilegios.

Abusar de los privilegios a nivel de sudoers es una técnica utilizada por los atacantes para elevar su nivel de acceso en un sistema comprometido. Si un atacante es capaz de obtener acceso a una cuenta con permisos de sudo en el archivo sudoers, puede ejecutar comandos con privilegios especiales y realizar acciones maliciosas en el sistema.

El comando “**sudo -l**” es utilizado para listar los permisos de sudo de un usuario en particular. Al ejecutar este comando, se muestra una lista de los comandos que el usuario tiene permiso para ejecutar y bajo qué condiciones.

Para prevenir el abuso de privilegios a nivel de sudoers, se recomienda mantener los permisos adecuados en el archivo sudoers y limitar el número de usuarios con permisos de sudo. Además, es importante monitorear regularmente el archivo sudoers y buscar cambios inesperados o sospechosos en su contenido.

A continuación, se os comparte el recurso GTFOBINS el cual utilizamos en esta clase para detectar comandos que potencialmente puedan ser explotados para elevar nuestro privilegio de usuario:

```bash
docker pull ubuntu:latest

docker run -dit --name ubuntuserver ubuntu

docker exec -it ubuntuserver bash

apt update
apt install -y nano sudo

sudo Crea un archivo en /etc/sudoers  Que es donde se gestionan las politicas sudo

#Cremos 2 usuarios para hacer pruebas
useradd -d /home/savitar -s /bin/bash -m savitar
useradd -d /home/manolo -s /bin/bash -m manolo

#Ponemos pass a los usuarios creados

passwd savitar

passwd manolo

#Editamos el archivo /etc/sudores, la forma correcta de editarlo es con el comando `visudo`

visudo  

root    ALL=(ALL:ALL) ALL

#info de cada elemento
usuario   hosts=(destiny_user:destiny_group)   comandos

#ejemplos
savitar  ALL=(root) NOPASSWD: /usr/bin/awk, /bin/cat #No requiere pass

savitar  ALL=(root)  /bin/ls, /usr/bin/man, /bin/cat #Si lo requiere

#Savitar puede ejecutar siendo manolo el comando nmap
savitar  ALL=(manolo) NOPASSWD: /usr/bin/nmap

#Ejecutando desde user saviar como manolo

sudo -u manolo nmap

```

![](../../../attachments/Pasted%20image%2020260219090714.png)