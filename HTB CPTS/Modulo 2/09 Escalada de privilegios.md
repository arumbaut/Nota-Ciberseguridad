---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/844"
author:
published:
created: 2026-06-03
description:
tags:
  - "clippings"
---
## Escalada de privilegios

---

Nuestro acceso inicial a un servidor remoto suele ser en el contexto de un usuario con pocos privilegios, lo que no nos daría acceso completo a través de la caja. Para obtener acceso completo, necesitaremos encontrar una vulnerabilidad interna/local que escalaría nuestros privilegios al `root` usuario en `Linux` o el `administrator` / `SYSTEM` usuario en `Windows`. Repasemos algunos métodos comunes para aumentar nuestros privilegios.

---

## Listas de verificación de PrivEsc

Una vez que obtenemos acceso inicial a una caja, queremos enumerarla minuciosamente para encontrar cualquier vulnerabilidad potencial que podamos explotar para lograr un nivel de privilegio más alto. Podemos encontrar muchas listas de verificación y hojas de trucos en línea que tienen una colección de comprobaciones que podemos ejecutar y los comandos para ejecutar estas comprobaciones. Un recurso excelente es [Trucos para hackear](https://book.hacktricks.xyz/), que tiene una excelente lista de verificación para ambos [Linux](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html) y [Windows](https://book.hacktricks.wiki/en/windows-hardening/checklist-windows-privilege-escalation.html) escalada de privilegios locales. Otro repositorio excelente es [Cargas útilesTodasLasCosas](https://github.com/swisskyrepo/PayloadsAllTheThings), que también tiene listas de verificación para ambos [Linux](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md) y [Windows](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md). Debemos comenzar a experimentar con varios comandos y técnicas y familiarizarnos con ellos para comprender múltiples debilidades que pueden llevar a aumentar nuestros privilegios.

---

## Guiones de enumeración

Muchos de los comandos anteriores se pueden ejecutar automáticamente con un script para revisar el informe y buscar debilidades. Podemos ejecutar muchos scripts para enumerar automáticamente el servidor ejecutando comandos comunes que devuelvan cualquier hallazgo interesante. Algunos de los scripts de enumeración comunes de Linux incluyen [LinEnum](https://github.com/rebootuser/LinEnum.git) y [Comprobador de privacidad de Linux](https://github.com/sleventyeleven/linuxprivchecker), y para Windows incluye [Cinturón de seguridad](https://github.com/GhostPack/Seatbelt) y [MANDÍBULAS](https://github.com/411Hall/JAWS).

Otra herramienta útil que podemos utilizar para la enumeración de servidores es la [Escalada de privilegios Awesome Scripts SUITE (PEASS)](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite), ya que está bien mantenido para mantenerse actualizado e incluye scripts para enumerar tanto Linux como Windows.

Nota: Estos scripts ejecutarán muchos comandos conocidos por identificar vulnerabilidades y crearán mucho "ruido" que puede activar software antivirus o software de monitoreo de seguridad que busca este tipo de eventos. Esto puede impedir que los scripts se ejecuten o incluso activar una alarma de que el sistema ha sido comprometido. En algunos casos, es posible que queramos hacer una enumeración manual en lugar de ejecutar scripts.

Tomemos un ejemplo de cómo ejecutar el script de Linux desde `PEASS` llamado `LinPEAS`:

```
shellsessionaalonso1190@htb[/htb]$ ./linpeas.sh
...SNIP...

Linux Privesc Checklist: https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist
 LEYEND:
  RED/YELLOW: 99% a PE vector
  RED: You must take a look at it
  LightCyan: Users with console
  Blue: Users without console & mounted devs
  Green: Common things (users, groups, SUID/SGID, mounts, .sh scripts, cronjobs)
  LightMangenta: Your username

====================================( Basic information )=====================================
OS: Linux version 3.9.0-73-generic
User & Groups: uid=33(www-data) gid=33(www-data) groups=33(www-data)
...SNIP...
```

Como podemos ver, una vez que se ejecuta el script, comienza a recopilar información y a mostrarla en un informe excelente. Analicemos algunas de las vulnerabilidades que deberíamos buscar en el resultado de estos scripts.

---

## Explotaciones del kernel

Siempre que nos encontremos con un servidor que ejecuta un sistema operativo antiguo, debemos comenzar por buscar posibles vulnerabilidades del kernel que puedan existir. Supongamos que el servidor no recibe mantenimiento con las últimas actualizaciones y parches. En ese caso, es probable que sea vulnerable a exploits específicos del kernel que se encuentran en versiones sin parches de Linux y Windows.

Por ejemplo, el script anterior nos mostró que la versión de Linux era `3.9.0-73-generic`. Si buscamos exploits en Google para esta versión o usamos `searchsploit`, encontraríamos un `CVE-2016-5195`, también conocido como `DirtyCow`. Podemos buscar y descargar el [Vaca sucia](https://github.com/dirtycow/dirtycow.github.io/wiki/PoCs) explotarlo y ejecutarlo en el servidor para obtener acceso root.

El mismo concepto también se aplica a Windows, ya que existen muchas vulnerabilidades en versiones anteriores o sin parches de Windows, con varias vulnerabilidades que pueden usarse para la escalada de privilegios. Debemos tener en cuenta que los exploits del kernel pueden causar inestabilidad en el sistema y debemos tener mucho cuidado antes de ejecutarlos en sistemas de producción. Lo mejor es probarlos en un entorno de laboratorio y ejecutarlos únicamente en sistemas de producción con aprobación explícita y coordinación con nuestro cliente.

---

## Software vulnerable

Otra cosa que debemos buscar es el software instalado. Por ejemplo, podemos utilizar el `dpkg -l` comando en Linux o mire `C:\Program Files` en Windows para ver qué software está instalado en el sistema. Deberíamos buscar exploits públicos para cualquier software instalado, especialmente si se utilizan versiones anteriores que contengan vulnerabilidades sin parches.

---

## Privilegios del usuario

Otro aspecto crítico a tener en cuenta después de obtener acceso a un servidor son los privilegios disponibles para el usuario al que tenemos acceso. Supongamos que se nos permite ejecutar comandos específicos como root (o como otro usuario). En ese caso, es posible que podamos escalar nuestros privilegios a usuarios root/del sistema u obtener acceso como un usuario diferente. A continuación se muestran algunas formas comunes de explotar ciertos privilegios de usuario:

1. Sudo
2. SUID
3. Privilegios de tokens de Windows

El `sudo` El comando en Linux permite a un usuario ejecutar comandos como un usuario diferente. Generalmente se utiliza para permitir que usuarios con privilegios inferiores ejecuten comandos como root sin darles acceso al usuario root. Esto generalmente se hace ya que los comandos específicos solo se pueden ejecutar como root 'como `tcpdump` ' o permitir al usuario acceder a ciertos directorios exclusivos de root. Podemos comprobar qué `sudo` privilegios que tenemos con el `sudo -l` comando:

```
shellsessionaalonso1190@htb[/htb]$ sudo -l

[sudo] password for user1:
...SNIP...

User user1 may run the following commands on ExampleServer:
    (ALL : ALL) ALL
```

El resultado anterior dice que podemos ejecutar todos los comandos con `sudo`, lo que nos da acceso completo y podemos utilizar el `su` comando con `sudo` Para cambiar al usuario root:

```
shellsessionaalonso1190@htb[/htb]$ sudo su -

[sudo] password for user1:
whoami
root
```

El comando anterior requiere una contraseña para ejecutar cualquier comando con `sudo`. Hay ciertas ocasiones en las que se nos puede permitir ejecutar ciertas aplicaciones, o todas las aplicaciones, sin tener que proporcionar una contraseña:

```
shellsessionaalonso1190@htb[/htb]$ sudo -l

    (user : user) NOPASSWD: /bin/echo
```

El `NOPASSWD` la entrada muestra que el `/bin/echo` El comando se puede ejecutar sin contraseña. Esto sería útil si obtuviéramos acceso al servidor a través de una vulnerabilidad y no tuviéramos la contraseña del usuario. Como dice `user`, podemos correr `sudo` como ese usuario y no como root. Para ello, podemos especificar el usuario con `-u user`:

```
shellsessionaalonso1190@htb[/htb]$ sudo -u user /bin/echo Hello World!

    Hello World!
```

Una vez que encontramos una aplicación particular, podemos ejecutarla `sudo`, podemos buscar formas de explotarlo para obtener un shell como usuario root. [GTFOBins](https://gtfobins.github.io/) contiene una lista de comandos y cómo se pueden explotar `sudo`. Podemos buscar la aplicación que tenemos `sudo` privilegio sobre, y si existe, puede indicarnos el comando exacto que debemos ejecutar para obtener acceso root usando el `sudo` privilegio que tenemos.

[LOLBAS](https://lolbas-project.github.io/#) También contiene una lista de aplicaciones de Windows que podemos aprovechar para realizar ciertas funciones, como descargar archivos o ejecutar comandos en el contexto de un usuario privilegiado.

---

## Tareas programadas

Tanto en Linux como en Windows, existen métodos para ejecutar scripts en intervalos específicos para llevar a cabo una tarea. Algunos ejemplos son tener un escaneo antivirus ejecutándose cada hora o un script de respaldo que se ejecuta cada 30 minutos. Generalmente hay dos formas de aprovechar las tareas programadas (Windows) o los trabajos cron (Linux) para escalar nuestros privilegios:

1. Agregar nuevas tareas programadas/trabajos cron
2. Engañarlos para que ejecuten un software malicioso

La forma más sencilla es comprobar si podemos añadir nuevas tareas programadas. En Linux, una forma común de mantener tareas programadas es a través de `Cron Jobs`. Hay directorios específicos que podemos utilizar para agregar nuevos trabajos cron si tenemos el `write` permisos sobre ellos. Estos incluyen:

1. `/etc/crontab`
2. `/etc/cron.d`
3. `/var/spool/cron/crontabs/root`

Si podemos escribir en un directorio llamado por un trabajo cron, podemos escribir un script bash con un comando de shell inverso, que debería enviarnos un shell inverso cuando se ejecute.

---

## Credenciales expuestas

A continuación, podemos buscar archivos que podamos leer y ver si contienen alguna credencial expuesta. Esto es muy común con `configuration` fișier, `log` archivos y archivos de historial de usuario (`bash_history` en Linux y `PSReadLine` en Windows). Los scripts de enumeración que analizamos al principio generalmente buscan contraseñas potenciales en archivos y nos las proporcionan, como se muestra a continuación:

```
shellsession...SNIP...
[+] Searching passwords in config PHP files
[+] Finding passwords inside logs (limit 70)
...SNIP...
/var/www/html/config.php: $conn = new mysqli(localhost, 'db_user', 'password123');
```

Como podemos ver, la contraseña de la base de datos ' `password123` ' está expuesto, lo que nos permitiría iniciar sesión en el local `mysql` bases de datos y busque información interesante. También podemos comprobarlo `Password Reuse`, ya que el usuario del sistema puede haber utilizado su contraseña para las bases de datos, lo que puede permitirnos utilizar la misma contraseña para cambiar a ese usuario, de la siguiente manera:

```
shellsessionaalonso1190@htb[/htb]$ su -

Password: password123
whoami

root
```

También podemos utilizar las credenciales de usuario para `ssh` en el servidor como ese usuario.

---

## Claves SSH

Por último, analicemos las claves SSH. Si tenemos acceso de lectura a través del `.ssh` directorio para un usuario específico, podemos leer sus claves ssh privadas que se encuentran en `/home/user/.ssh/id_rsa` o `/root/.ssh/id_rsa`, y úselo para iniciar sesión en el servidor. Si podemos leer el `/root/.ssh/` directorio y puede leer el `id_rsa` archivo, podemos copiarlo a nuestra máquina y usar el `-i` bandera para iniciar sesión con ella:

```
shellsessionaalonso1190@htb[/htb]$ vim id_rsa
aalonso1190@htb[/htb]$ chmod 600 id_rsa
aalonso1190@htb[/htb]$ ssh root@10.10.10.10 -i id_rsa

root@10.10.10.10#
```

Tenga en cuenta que utilizamos el comando 'chmod 600 id\_rsa' en la clave después de crearla en nuestra máquina para cambiar los permisos del archivo para que sean más restrictivos. Si las claves ssh tienen permisos laxos, es decir, pueden ser leídas por otras personas, el servidor ssh impediría que funcionen.

Si nos encontramos con acceso de escritura a un usuario `/.ssh/` directorio, podemos colocar nuestra clave pública en el directorio ssh del usuario en `/home/user/.ssh/authorized_keys`. Esta técnica se utiliza generalmente para obtener acceso ssh después de obtener un shell como ese usuario. La configuración SSH actual no aceptará claves escritas por otros usuarios, por lo que solo funcionará si ya hemos obtenido el control sobre ese usuario. Primero debemos crear una nueva clave con `ssh-keygen` y el `-f` bandera para especificar el archivo de salida:

```
shellsessionaalonso1190@htb[/htb]$ ssh-keygen -f key

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): *******
Enter same passphrase again: *******

Your identification has been saved in key
Your public key has been saved in key.pub
The key fingerprint is:
SHA256:...SNIP... user@parrot
The key's randomart image is:
+---[RSA 3072]----+
|   ..o.++.+      |
...SNIP...
|     . ..oo+.    |
+----[SHA256]-----+
```

Esto nos dará dos archivos: `key` (que usaremos con `ssh -i`) și `key.pub`, que copiaremos a la máquina remota. Vamos a copiar `key.pub`, luego en la máquina remota, lo agregaremos a `/root/.ssh/authorized_keys`:

```
shellsessionuser@remotehost$ echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys
```

Ahora, el servidor remoto debería permitirnos iniciar sesión como ese usuario utilizando nuestra clave privada:

```
shellsessionaalonso1190@htb[/htb]$ ssh root@10.10.10.10 -i key

root@remotehost#
```

Como podemos ver, ahora podemos acceder por SSH como usuario `root`. El [Escalada de privilegios de Linux](https://academy.hackthebox.com/module/details/51) y el [Escalada de privilegios de Windows](https://academy.hackthebox.com/module/details/67) Los módulos brindan más detalles sobre cómo utilizar cada uno de estos métodos para la escalada de privilegios y muchos otros también.

