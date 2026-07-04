---
title: "Escaneo de servicios | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/726"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Escaneo de servicios

---

¡Estamos listos para dar un paso más y comenzar a explorar una máquina! Lo primero que debemos hacer es identificar el sistema operativo y cualquier servicio disponible que pueda estar ejecutándose. Un servicio es una aplicación que se ejecuta en una computadora y que realiza alguna función útil para otros usuarios o computadoras. A estas máquinas especializadas que alojan estos servicios útiles las llamamos "servidores" en lugar de estaciones de trabajo, lo que permite a los usuarios interactuar con estos diversos servicios y consumirlos. Lo que nos interesa son los servicios que han sido mal configurados o tienen una vulnerabilidad. En lugar de realizar las acciones esperadas como parte del servicio, nos interesa ver si podemos obligar al servicio a realizar alguna acción no deseada que respalde nuestros objetivos, como ejecutar un comando de nuestra elección.

A las computadoras se les asigna una dirección IP, lo que permite identificarlas de forma única y acceder a ellas en una red. A los servicios que se ejecutan en estas computadoras se les puede asignar un número de puerto para que el servicio sea accesible. Como se discutió anteriormente, los números de puerto varían de 1 a 65.535, y el rango de puertos conocidos de 1 a 1.023 está reservado para servicios privilegiados. El puerto 0 es un puerto reservado en redes TCP/IP y no se utiliza en mensajes TCP o UDP. Si algo intenta vincularse al puerto 0 (como un servicio), se vinculará al siguiente puerto disponible por encima del puerto 1024 porque el puerto 0 se trata como un puerto "comodín".

Para acceder a un servicio de forma remota, necesitamos conectarnos utilizando la dirección IP y el número de puerto correctos y utilizar un idioma que el servicio entienda. Examinar manualmente los 65.535 puertos en busca de servicios disponibles sería laborioso, por lo que se han creado herramientas para automatizar este proceso y escanear la gama de puertos por nosotros. Una de las herramientas de escaneo más utilizadas es Nmap (Network Mapper).

---

## NMAP

Comencemos con el escaneo más básico. Supongamos que queremos realizar un escaneo básico contra un objetivo que reside en 10.129.42.253. Para hacer esto debemos escribir `nmap 10.129.42.253` y pulsa devolver. Vemos que el `Nmap` El escaneo se completó muy rápidamente. Esto se debe a que si no especificamos ninguna opción adicional, Nmap solo escaneará los 1000 puertos más comunes de forma predeterminada. La salida de escaneo revela que los puertos 21, 22, 80, 139 y 445 están disponibles.

```
shellsessionaalonso1190@htb[/htb]$ nmap 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:07 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).
Not shown: 995 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 2.19 seconds
```

Bajo el `PORT` encabezado, también nos dice que estos son puertos TCP. Por defecto, `Nmap` realizará un escaneo TCP a menos que se le solicite específicamente que realice un escaneo UDP.  
El `STATE` El encabezado confirma que estos puertos están abiertos. A veces veremos otros puertos listados que tienen un estado diferente, como por ejemplo `filtered`. Esto puede suceder si un firewall solo permite el acceso a los puertos desde direcciones específicas.  
El `SERVICE` el encabezado nos dice que el nombre del servicio normalmente se asigna al número de puerto específico. Sin embargo, el escaneo predeterminado no nos dirá qué está escuchando en ese puerto. Hasta que instruyamos `Nmap` Para interactuar con el servicio e intentar obtener información de identificación, podría ser un servicio completamente diferente.

A medida que nos familiaricemos, notaremos que varios puertos se asocian comúnmente con Windows o Linux. Por ejemplo, el puerto 3389 es el puerto predeterminado para los servicios de escritorio remoto y es una excelente indicación de que el objetivo es una máquina Windows. En nuestro escenario actual, el hecho de que el puerto 22 (SSH) esté disponible indica que el destino ejecuta Linux/Unix, pero este servicio también se puede configurar en Windows. Ejecutemos un proceso más avanzado `Nmap` escanee y recopile más información sobre el dispositivo de destino.

Podemos utilizar el `-sC` parámetro para especificar eso `Nmap` Se deben utilizar scripts para intentar obtener información más detallada. El `-sV` instrucciones de parámetros `Nmap` para realizar un escaneo de versiones. En este escaneo, Nmap tomará huellas dactilares de los servicios en el sistema de destino e identificará el protocolo del servicio, el nombre de la aplicación y la versión. El escaneo de versiones está respaldado por una base de datos completa de más de 1000 firmas de servicios. Finalmente, `-p-` le dice a Nmap que queremos escanear los 65.535 puertos TCP.

```
shellsessionaalonso1190@htb[/htb]$ nmap -sV -sC -p- 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:18 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).
Not shown: 65530 closed ports
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x    2 ftp      ftp          4096 Feb 25 19:25 pub
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.14.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
80/tcp  open  http        Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: PHP 7.4.3 - phpinfo()
139/tcp open  netbios-ssn Samba smbd 4.6.2
445/tcp open  netbios-ssn Samba smbd 4.6.2
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_nbstat: NetBIOS name: GS-SVCSCAN, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-02-25T21:21:51
|_  start_date: N/A

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 233.68 seconds
```

Esto devuelve mucha más información. Vemos que tomó mucho más tiempo escanear 65.535 puertos que 1.000 puertos. El `-sC` y `-sV` Las opciones también aumentan la duración de un escaneo, ya que en lugar de realizar un simple protocolo de enlace TCP, realizan muchas más comprobaciones. Observamos que esta vez hay un encabezado VERSIÓN, que informa la versión del servicio y el sistema operativo si es posible identificarlo.

Hasta ahora sabemos que el sistema operativo es Ubuntu Linux. Las versiones de la aplicación también pueden ayudar a revelar la versión del sistema operativo de destino. Tomemos como ejemplo OpenSSH. Vemos que la versión reportada es `OpenSSH 8.2p1 Ubuntu 4ubuntu0.1`. De la inspección de otros paquetes SSH de Ubuntu [registros de cambios](https://launchpad.net/ubuntu/yakkety/+source/openssh/+changelog), vemos que la versión de lanzamiento toma el formato `1:7.3p1-1ubuntu0.1`. Actualizando nuestra versión para que se ajuste a este formato, obtenemos `1:8.2p1-4ubuntu0.1`. Una búsqueda rápida de esta versión en línea revela que está incluida en Ubuntu Linux Focal Fossa 20.04.

![Resultados de búsqueda de Google para '1:8.2p1-4ubuntu0.1 release' que muestran enlaces al paquete OpenSSH en Launchpad.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/google1.png)

Otra búsqueda rápida revela que la fecha de lanzamiento de este sistema operativo es el 23 de abril de 2020.

![Los resultados de búsqueda de Google para 'Fecha de lanzamiento de Ubuntu focus 20.04' muestran el 23 de abril de 2020 como fecha de lanzamiento.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/google2.png)

Sin embargo, vale la pena señalar que esta técnica de referencia cruzada no es del todo confiable, ya que es posible instalar paquetes de aplicaciones más recientes en una versión anterior del sistema operativo. El escaneo del script `-sC` causas de bandera `Nmap` para informar los encabezados del servidor `http-server-header` página y el título de la página `http-title` para cualquier página web alojada en el servidor web. El título de la página web `PHP 7.4.3 - phpinfo()` indica que se trata de un archivo PHPInfo, que a menudo se crea manualmente para confirmar que PHP se ha instalado correctamente. El título (y la página PHPInfo) también revelan la versión de PHP, lo cual vale la pena señalar si es vulnerable.

http://10.129.42.253/index.php

![Tabla de información de PHP versión 7.4.3 que muestra detalles del sistema, fecha de compilación, API del servidor y rutas de configuración.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/phpinfo.png)

#### Scripts de Nmap

Especifica `-sC` ejecutará muchos scripts predeterminados útiles contra un objetivo, pero hay casos en los que se requiere ejecutar un script específico. Por ejemplo, en un ámbito de evaluación, es posible que se nos solicite auditar una instalación grande de Citrix. Podríamos usarlo [esto](https://raw.githubusercontent.com/cyberstruggle/DeltaGroup/master/CVE-2019-19781/CVE-2019-19781.nse) `Nmap` script para auditar la grave vulnerabilidad de Citrix NetScaler ([CVE-2019–19781](https://www.rapid7.com/blog/post/2020/01/17/active-exploitation-of-citrix-netscaler-cve-2019-19781-what-you-need-to-know/)), mientras `Nmap` También tiene otros scripts para auditar una instalación de Citrix.

```
shellsessionaalonso1190@htb[/htb]$ locate scripts/citrix

/usr/share/nmap/scripts/citrix-brute-xml.nse
/usr/share/nmap/scripts/citrix-enum-apps-xml.nse
/usr/share/nmap/scripts/citrix-enum-apps.nse
/usr/share/nmap/scripts/citrix-enum-servers-xml.nse
/usr/share/nmap/scripts/citrix-enum-servers.nse
```

La sintaxis para ejecutar un script Nmap es `nmap --script <script name> -p<port> <host>`.

`Nmap` Los scripts son una excelente manera de mejorar la funcionalidad de nuestros escaneos, y la inspección de las opciones disponibles dará sus frutos. Echa un vistazo al [Enumeración de red con Nmap](https://academy.hackthebox.com/module/details/19) módulo para un estudio más detallado del `Nmap` herramienta.

---

## Ataque a los servicios de red

#### Agarrando pancartas

Como se mencionó anteriormente, la captura de banners es una técnica útil para tomar huellas dactilares de un servicio rápidamente. A menudo, un servicio buscará identificarse mostrando un banner una vez que se inicia una conexión. Nmap intentará capturar los banners si la sintaxis `nmap -sV --script=banner <target>` se especifica. También podemos intentar esto manualmente usando `Netcat`. Tomemos otro ejemplo, utilizando el `nc` versión de `Netcat`:

```
shellsessionaalonso1190@htb[/htb]$ nc -nv 10.129.42.253 21

(UNKNOWN) [10.129.42.253] 21 (ftp) open
220 (vsFTPd 3.0.3)
```

Esto revela que la versión de `vsFTPd` en el servidor está `3.0.3`. También podemos automatizar este proceso usando `Nmap's` potente motor de scripts: `nmap -sV --script=banner -p21 10.10.10.0/24`.

#### FTP

Vale la pena familiarizarse con FTP, ya que es un protocolo estándar y este servicio a menudo puede contener datos interesantes. A `Nmap` El escaneo del puerto predeterminado para FTP (21) revela la instalación de vsftpd 3.0.3 que identificamos previamente. Además, también informa que la autenticación anónima está habilitada y que a `pub` El directorio está disponible.

```
shellsessionaalonso1190@htb[/htb]$ nmap -sC -sV -p21 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2020-12-20 00:54 GMT
Nmap scan report for 10.129.42.253
Host is up (0.081s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x    2 ftp      ftp          4096 Dec 19 23:50 pub
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.14.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.78 seconds
```

Conectémonos al servicio usando el `ftp` utilidad de línea de comandos.

```
shellsessionaalonso1190@htb[/htb]$ ftp -p 10.129.42.253

Connected to 10.129.42.253.
220 (vsFTPd 3.0.3)
Name (10.129.42.253:user): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.

ftp> ls
227 Entering Passive Mode (10,129,42,253,158,60).
150 Here comes the directory listing.
drwxr-xr-x    2 ftp      ftp          4096 Feb 25 19:25 pub
226 Directory send OK.

ftp> cd pub
250 Directory successfully changed.

ftp> ls
227 Entering Passive Mode (10,129,42,253,182,129).
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            18 Feb 25 19:25 login.txt
226 Directory send OK.

ftp> get login.txt
local: login.txt remote: login.txt
227 Entering Passive Mode (10,129,42,253,181,53).
150 Opening BINARY mode data connection for login.txt (18 bytes).
226 Transfer complete.
18 bytes received in 0.00 secs (165.8314 kB/s)

ftp> exit
221 Goodbye.
```

En el shell anterior, vemos que FTP admite comandos comunes como `cd` y `ls` y nos permite descargar archivos usando el `get` comando. Inspección de lo descargado `login.txt` revela credenciales que podríamos utilizar para ampliar nuestro acceso al sistema.

```
shellsessionaalonso1190@htb[/htb]$ cat login.txt 

admin:ftp@dmin123
```

---

#### SMB

SMB (Server Message Block) es un protocolo predominante en las máquinas Windows que proporciona muchos vectores para el movimiento vertical y lateral. Los datos confidenciales, incluidas las credenciales, pueden estar en archivos compartidos de red y algunas versiones de SMB pueden ser vulnerables a exploits de RCE, como [Azul eterno](https://www.avast.com/c-eternalblue). Es fundamental enumerar cuidadosamente esta considerable superficie de ataque potencial. `Nmap` tiene muchos scripts para enumerar SMB, como por ejemplo [smb-os-discovery.nse](https://nmap.org/nsedoc/scripts/smb-os-discovery.html), que interactuará con el servicio SMB para extraer la versión del sistema operativo reportada.

```
shellsessionaalonso1190@htb[/htb]$ nmap --script smb-os-discovery.nse -p445 10.10.10.40

Starting Nmap 7.91 ( https://nmap.org ) at 2020-12-27 00:59 GMT
Nmap scan report for doctors.htb (10.10.10.40)
Host is up (0.022s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

Host script results:
| smb-os-discovery: 
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: CEO-PC
|   NetBIOS computer name: CEO-PC\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2020-12-27T00:59:46+00:00

Nmap done: 1 IP address (1 host up) scanned in 2.71 seconds
```

En este caso, el host ejecuta un sistema operativo Windows 7 heredado y podríamos realizar una enumeración adicional para confirmar si es vulnerable a EternalBlue. El marco Metasploit tiene varios [módulos](https://www.rapid7.com/db/modules/exploit/windows/smb/ms17_010_eternalblue/) para EternalBlue que se puede utilizar para validar la vulnerabilidad y explotarla, como veremos en una próxima sección. Podemos ejecutar un escaneo contra nuestro objetivo para esta sección del módulo para recopilar información del servicio SMB. Podemos determinar que el host ejecuta un kernel de Linux, Samba versión 4.6.2, y el nombre de host es GS-SVCSCAN.

```
shellsessionaalonso1190@htb[/htb]$ nmap -A -p445 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:29 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).

PORT    STATE SERVICE     VERSION
445/tcp open  netbios-ssn Samba smbd 4.6.2
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 2.6.32 (95%), Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (94%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%), Adtran 424RG FTTH gateway (92%), Linux 2.6.39 - 3.2 (92%), Linux 3.1 - 3.2 (92%), Linux 3.2 - 4.9 (92%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops

Host script results:
|_nbstat: NetBIOS name: GS-SVCSCAN, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-02-25T21:30:06
|_  start_date: N/A

TRACEROUTE (using port 445/tcp)
HOP RTT       ADDRESS
1   111.62 ms 10.10.14.1
2   111.89 ms 10.129.42.253

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.72 seconds
```

---

#### Acciones

SMB permite a los usuarios y administradores compartir carpetas y hacer que otros usuarios puedan acceder a ellas de forma remota. A menudo, estos recursos compartidos contienen archivos que contienen información confidencial, como contraseñas. Una herramienta que puede enumerar e interactuar con acciones de PYMES es [cliente smb](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html). El `-L` flag especifica que queremos recuperar una lista de recursos compartidos disponibles en el host remoto, mientras `-N` suprime el mensaje de contraseña.

```
shellsessionaalonso1190@htb[/htb]$ smbclient -N -L \\\\10.129.42.253

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    users           Disk      
    IPC$            IPC       IPC Service (gs-svcscan server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available
```

Esto revela la participación no predeterminada `users`. Intentemos conectarnos como usuario invitado.

```
shellsessionaalonso1190@htb[/htb]$ smbclient \\\\10.129.42.253\\users

Enter WORKGROUP\users's password: 
Try "help" to get a list of possible commands.

smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*

smb: \> exit
```

El `ls` El comando generó un mensaje de acceso denegado, lo que indica que no se permite el acceso de invitados. Intentemos nuevamente usar credenciales para el usuario bob (`bob:Welcome1`).

```
shellsessionaalonso1190@htb[/htb]$ smbclient -U bob \\\\10.129.42.253\\users

Enter WORKGROUP\bob's password: 
Try "help" to get a list of possible commands.

smb: \> ls
  .                                   D        0  Thu Feb 25 16:42:23 2021
  ..                                  D        0  Thu Feb 25 15:05:31 2021
  bob                                 D        0  Thu Feb 25 16:42:23 2021

        4062912 blocks of size 1024. 1332480 blocks available
        
smb: \> cd bob

smb: \bob\> ls
  .                                   D        0  Thu Feb 25 16:42:23 2021
  ..                                  D        0  Thu Feb 25 16:42:23 2021
  passwords.txt                       N      156  Thu Feb 25 16:42:23 2021

        4062912 blocks of size 1024. 1332480 blocks available
        
smb: \bob\> get passwords.txt 
getting file \bob\passwords.txt of size 156 as passwords.txt (0.3 KiloBytes/sec) (average 0.3 KiloBytes/sec)
```

Obtuvimos acceso con éxito a la `users` compartir usando credenciales y obtuvo acceso al interesante archivo `passwords.txt`, que se puede descargar con el `get` comando.

---

#### SNMP

Las cadenas de la comunidad SNMP proporcionan información y estadísticas sobre un enrutador o dispositivo, lo que nos ayuda a obtener acceso a él. Las cadenas de comunidad predeterminadas del fabricante de `public` y `private` A menudo no cambian. En las versiones 1 y 2c de SNMP, el acceso se controla mediante una cadena comunitaria de texto simple y, si conocemos el nombre, podemos acceder a ella. El cifrado y la autenticación solo se agregaron en la versión 3 de SNMP. Se puede obtener mucha información del SNMP. El examen de los parámetros del proceso podría revelar credenciales pasadas en la línea de comando, que podrían reutilizarse para otros servicios accesibles externamente dada la prevalencia de la reutilización de contraseñas en entornos empresariales. También se puede revelar información de enrutamiento, servicios vinculados a interfaces adicionales y la versión del software instalado.

```
shellsessionaalonso1190@htb[/htb]$ snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0

iso.3.6.1.2.1.1.5.0 = STRING: "gs-svcscan"
```
```
shellsessionaalonso1190@htb[/htb]$ snmpwalk -v 2c -c private  10.129.42.253 

Timeout: No Response from 10.129.42.253
```

Una herramienta como [onesixtyone](https://github.com/trailofbits/onesixtyone) se puede utilizar para forzar los nombres de las cadenas comunitarias utilizando un archivo de diccionario de cadenas comunitarias comunes como `dict.txt` archivo incluido en el repositorio de GitHub de la herramienta.

```
shellsessionaalonso1190@htb[/htb]$ onesixtyone -c dict.txt 10.129.42.254

Scanning 1 hosts, 51 communities
10.129.42.254 [public] Linux gs-svcscan 5.4.0-66-generic #74-Ubuntu SMP Wed Jan 27 22:54:38 UTC 2021 x86_64
```

---

## Conclusión

El escaneo y enumeración de servicios es un tema amplio sobre el que aprenderemos más a medida que avancemos. Los aspectos que hemos cubierto aquí se aplican a muchas redes, incluidas las máquinas HTB.

## Conéctese a HTB

Habilite soluciones paso a paso

PRO