- Tags #metasploit 

**Metasploit** es una plataforma de pruebas de penetración (Penetration Testing Framework) que se utiliza para realizar pruebas de seguridad en sistemas y aplicaciones. Esta plataforma es ampliamente utilizada por investigadores de seguridad, pentesters y profesionales de la seguridad para descubrir vulnerabilidades y realizar pruebas de explotación de vulnerabilidades. Metasploit se basa en un conjunto de herramientas de seguridad que incluyen un framework de desarrollo de exploits, un motor de base de datos de vulnerabilidades y una colección de módulos de explotación de vulnerabilidades.

En términos prácticos, Metasploit se utiliza para probar la seguridad de un sistema o aplicación mediante la realización de pruebas de penetración, con el objetivo de identificar y explotar vulnerabilidades de seguridad. Para hacer esto, Metasploit proporciona una gran cantidad de exploits, payloads y módulos de post-explotación, que pueden ser utilizados por los profesionales de seguridad para identificar vulnerabilidades y explotarlas. Al utilizar Metasploit, los profesionales de la seguridad pueden simular ataques reales y descubrir vulnerabilidades en sistemas y aplicaciones antes de que los atacantes malintencionados puedan hacerlo, lo que les permite corregir las vulnerabilidades y mejorar la seguridad de sus sistemas.

En esta clase, veremos cómo utilizar algunas de las funcionalidades de esta herramienta.

Correr el Measploit de forma correcta
```bash
sudo msfdb run
```

Modulos de Metasploit 
```bash
❯ cd /usr/share/metasploit-framework/modules  
❯ ls
 auxiliary   encoders   evasion   exploits   nops   payloads   post   README.md

```

**Hacer búsquedas con metasploit:** #metasploit_search  
```bash
[msf](Jobs:0 Agents:0)>>search [payloads,exploits,encoders,auxiliare, palabra,OS,etc]

msf >  search -h
Usage: search [<options>] [<keywords>:<value>]
#Para ver las keywords leemos la ayuda que nos muestra

OPTIONS:
-a, --add <name>          Add a workspace.
-d, --delete <name>       Delete a workspace.
-D, --delete-all          Delete all workspaces.
-h, --help                Help banner.
-l, --list                List workspaces.
-r, --rename <old> <new>  Rename a workspace.
-S, --search <name>       Search for a workspace.
-v, --list-verbose        List workspaces verbosely.

#[Ejemplos]
msf >  search platform:Windows
msf >  search cve:2009 type:exploit
msf >  search cve:2009 type:exploit platform:-linux
msf >  search cve:2009 -s name
msf >  search type:exploit -s type -r
msf >  search att&ck:T1059
```


**Crear un espacio de Trabajo** para diferenciar las auditorias que se hagan #metasploit_work_space

```bash
[msf](Jobs:0 Agents:0)>>workspace   #Lista workspaces
[msf](Jobs:0 Agents:0)>>workspace -a Windows  #Crea el WorkSpace Windows
[msf](Jobs:0 Agents:0)>>workspace Linux  #Cambial al WorkSpace Linux 
[msf](Jobs:0 Agents:0)>>workspace -d Linux  #Cambial al WorkSpace Linux 

#[Opciones]
-a, --add <name>          Add a workspace.
-d, --delete <name>       Delete a workspace.
-D, --delete-all          Delete all workspaces.
-h, --help                Help banner.
-l, --list                List workspaces.
-r, --rename <old> <new>  Rename a workspace.
-S, --search <name>       Search for a workspace.
-v, --list-verbose        List workspaces verbosely.

```

**Usar un modulo en metasploit** #metasploit_use_module
```bash
msf >  auxiliary/scanner/discovery/arp_sweep 
```

**Ver las opciones de un modulo** #metasploit_options_module
```bash
msf >  auxiliary/scanner/discovery/arp_sweep 
msf >  show options
msf >  show advanced options #Muestra opciones avanzadas

msf > info #Muestra la descripcion del modulo 
msf > info -d #Nos genera un manual de uso del modulo en html 

```

**Establecer las variables requeridas en las opciones de un modulo** #metasploit_set_values
```bash
msf > auxiliary/scanner/discovery/arp_sweep
msf > set RHOST 192.168.111.0/24
```

**Ejecutar un modulo seleccionado** #metasploit_ejecutar_modulo #metasploit_ejecutar

```bash
msf > run
```

**Ver los equipos detectados para un espacio de trabajo** #metasploit_host
```bash
msf > hosts
```

**Ver los servicios detectados para un espacio de trabajo** #metasploit_services
```bash
msf > services
```

**Importar a metasploit la salida de nmap** #metasploit_nmap
```bash
nmap -p- -sS --open --min-rate 5000 -vvvv -Pn -n 172.17.0.2 -oX allPorts 

#Para detectar el sistema operativo
nmap -p- -sS -O --open --min-rate 5000 -vvvv -Pn -n 172.17.0.2 -oX allPorts 
nmap -A ip -oX OSScan

#Importamos
msf > db_import /home/alex/work/allPorts
msf > db_import /home/alex/work/OSScan
msf > hosts
msf > services 
```

**Muestrame solo algunos campos de los host** 
```bash
msf > hosts -C os_name,purpose
```

![](../../../attachments/Pasted%20image%2020260225231601.png)