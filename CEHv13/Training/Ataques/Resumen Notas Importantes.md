**Non-Repudiation** 
El no repudio es una forma de garantizar que el remitente de un mensaje no pueda negar posteriormente haberlo enviado y que el destinatario no pueda negar haberlo recibido

#### :TiJewishStar: Payment Card Industry Data Security Standard (PCI DSS)  
Norma para la proteccion de  información de titulares de tarjetas de las principales tarjetas de débito, crédito, prepago, monedero electrónico, cajero automático y punto de venta

:TiJewishStar: ISO/IEC 27001:2022  
normas internacionales para los Sistemas de Gestión de Seguridad de la Información (SGSI). Estas especifican los requisitos y el marco para establecer, implementar, mantener y mejorar continuamente un SGSI con el fin de garantizar la confidencialidad, integridad y disponibilidad de la información.

#### :TiJewishStar:Health Insurance Portability and Accountability Act (HIPAA) 
Proporciona protecciones federales para la información de salud individualmente identificable

#### The Digital Millennium Copyright Act (DMCA) 
La **DMCA** (Ley de Derechos de Autor del Milenio Digital) es una ley estadounidense de derechos de autor que implementa dos tratados de 1996 de la Organización Mundial de la Propiedad Intelectual (OMPI)

#### :TiJewishStar: The Federal Information Security Management Act (FISMA) 

FISMA proporciona un marco integral para asegurar la efectividad de los controles de seguridad de la información sobre los recursos de información que respaldan las operaciones y activos federales. 

General Data Protection Regulation (GDPR)
Es una de las leyes de privacidad y seguridad más estrictas a nivel mundial.

|                  |                                                                                                  |                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| **Operador**     | **Descripción**                                                                                  | **Ejemplo**                                                 |
| **site:**        | Restringe los resultados a un sitio o dominio específico.                                        | games site:www.certifiedhacker.com                          |
| **allinurl:**    | Muestra solo páginas que contienen todos los términos en la URL.                                 | allinurl: google career                                     |
| **inurl:**       | Muestra solo páginas que contienen el término especificado en la URL.                            | inurl:copy site:www.google.com                              |
| **intext:**      | Muestra resultados con el término especificado dentro del cuerpo de la página.                   | intext:"vpn configuration"                                  |
| **allintitle:**  | Muestra solo páginas cuyo título contiene todos los términos especificados.                      | allintitle: detect malware                                  |
| **intitle:**     | Muestra solo páginas cuyo título contiene el término especificado.                               | malware detection intitle:help                              |
| **inanchor:**    | Muestra páginas con enlaces cuyo texto de anclaje contiene el término especificado.              | Anti-virus inanchor:Norton                                  |
| **allinanchor:** | Muestra páginas cuyos enlaces contienen todos los términos especificados en el texto de anclaje. | allinanchor: best cloud service provider                    |
| **cache:**       | Muestra la versión en caché de una página almacenada por Google.                                 | cache:www.eff.org                                           |
| **link:**        | Encuentra páginas que enlazan a un sitio o página específica.                                    | link:www.googleguide.com                                    |
| **related:**     | Muestra sitios web similares o relacionados al URL especificado.                                 | related:www.microsoft.com                                   |
| **info:**        | Muestra información sobre una página web específica.                                             | info:gothotel.com                                           |
| **location:**    | Devuelve resultados basados en una ubicación específica.                                         | location: 4 seasons restaurant                              |
| **filetype:**    | Busca archivos con una extensión específica.                                                     | jasmine filetype:jpg                                        |
| **source:**      | Muestra información de un sitio web específico en Google News.                                   | Malware news source:"Hacker News"                           |
| **phonebook:**   | Encuentra números telefónicos de personas u organizaciones.                                      | phonebook:Sundar Pichai                                     |
| **before:**      | Filtra resultados publicados antes de una fecha específica.                                      | ransomware before:2020-06-29                                |
| **after:**       | Filtra resultados publicados después de una fecha específica.                                    | site:wikipedia.org after:2023-01-01 artificial intelligence |
### **Tools to Search Company`s Sub domains**
**Netcraft Source:**
**▪ DNSdumpster**
**▪ Pentest-Tools Find Subdomains**
**Recon-ng**: Para realizar reconocimientos basados en la web
**theHarvester**: Para extraer direcciones de correo electrónico relacionadas con el dominio objetivo
**Sherlock**: Para buscar un nombre de usuario objetivo en una gran cantidad de sitios de redes sociales
**▪ Censys** :  Monitorizar la infraestructura de TI objetivo y descubrir diversos dispositivos conectados a Internet,
**▪ BuzzSumo:** Encuentra el contenido más compartido de un tema, autor o dominio. Muestra la actividad compartida en las principales redes sociales, como Twitter, Facebook, LinkedIn, Google Plus
**Whois Footprinting**: Para consultar bases de datos que almacenan a los usuarios registrados o asignatarios de un recurso de Internet, como un nombre de dominio, un bloque de direcciones IP o un sistema autónomo
**▪ OSINT Framework** 
**▪ People Search Service - Spokeo**: para buscar a miembros de la organización objetivo.  Obtienen información como números de teléfono, direcciones de correo electrónico, historial de direcciones, edad, fecha de nacimiento, familiares, perfiles sociales y registros judiciales.

### **DNS**

| **Tipo de Registro** | **Descripción (en español)**                                   | **Explicación**                                                                                                           |
| -------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **A**                | Apunta a la dirección IP de un host (IPv4).                    | Utilizado para dirigir un nombre de dominio a una dirección IP (ej. 192.168.1.1).                                         |
| **AAAA**             | Apunta a la dirección IPv6 de un host.                         | Similar al tipo A, pero para direcciones IPv6.                                                                            |
| **MX**               | Apunta al servidor de correo de un dominio.                    | Especifica qué servidor se encarga de recibir correos electrónicos del dominio.                                           |
| **NS**               | Apunta al servidor de nombres del host.                        | Indica los servidores que tienen autoridad para ese dominio.                                                              |
| **CNAME**            | Alias canónico, permite alias para un host.                    | Redirige un nombre a otro nombre (por ejemplo, www a dominio.com).                                                        |
| **SOA**              | Indica la autoridad para un dominio.                           | Contiene información administrativa del dominio, como el servidor principal y los tiempos de actualización.               |
| **SRV**              | Registros de servicio.                                         | Utilizado para servicios específicos (como VoIP o mensajería instantánea), indicando el puerto y protocolo.               |
| **PTR**              | Mapea una dirección IP a un nombre de host.                    | Se usa en búsquedas inversas de DNS (de IP a nombre de dominio).                                                          |
| **RP**               | Persona responsable.                                           | Contiene información sobre el responsable técnico del dominio.                                                            |
| **HINFO**            | Información del host, incluye tipo de CPU y sistema operativo. | Aporta datos sobre la infraestructura del host. No se usa frecuentemente por razones de seguridad.                        |
| **TXT**              | Registros de texto no estructurado.                            | Permite almacenar información arbitraria en forma de texto, muy utilizado para verificación y seguridad (como SPF, DKIM). |
**DNS Interrogation Tools** 
**▪ SecurityTrails 
Es una herramienta avanzada de enumeración de DNS capaz de crear un mapa DNS de la red del dominio objetivo

**▪ Fierce**
Reconocimiento de DNS que se utiliza para escanear y recopilar información crucial sobre el dominio objetivo

TCP Conection
==THREE WAY HANSHAKE==                                               
SYNC→
      ←SYNC+ACK
ACK   →

FIN DE CONECCION 
FIN →
     ←ACK
     ←FIN
ACK→

Scanning Tools

**Nmap** 
Notas importantes parametros
-F : escanea solo los 100 puesrtos mas comunes
-p- : escanea los 65535 puertos  [conocidos: 0  -  1023 , Registrados : 1024  -  49.151, dinámicos  o  privados: 49.152  -  65.535]
-f : Frangmntar paquetes
==Permite descubrir hosts, puertos y servicios en una red informática, creando así un "mapa" de la red.==

**Escaneo ARP Ping**
==**nmap -sn -PR target**==
**-sn** es el comando de Nmap que **se utiliza para deshabilitar el escaneo de puertos**

**Escaneo UDP Ping**
**nmap -sn -PU target**

**Escaneo ICMP ECHO Ping**
**nmap -sn -PE target**

==**ICMP ECHO Ping Sweep (también conocido como barrido ICMP) **==
**nmap -sn -PE** **target** **10.10.1.5-24**

**Escaneo ICMP Timestamp Ping**
**nmap -sn -PM** **target** **10.10.1.5**


==**TCP SYN Ping Scan**==
**nmap -sn -PS 10.10.1.5**
==El TCP SYN ping es una técnica de descubrimiento de hosts que se utiliza para sondear diferentes puertos y determinar si están en línea, así como para identificar si existen reglas de firewall activas.==

**TCP ACK Ping Scan**
==**La recepción del paquete RST por parte del atacante indica que el host está activo
**nmap -sn -PA 10.10.1.5**

**IP Protocol Ping Scan**
**nmap -sn -PO 10.10.1.5**

**▪ Hping3**
==Es una herramienta orientada a la línea de comandos para el escaneo de redes y la creación de paquetes para el protocolo TCP/IP que envía solicitudes de eco ICMP y admite los protocolos TCP, UDP, ICMP y raw-IP. Realiza auditorías de seguridad de redes, pruebas de cortafuegos, descubrimiento manual de MTU de ruta, traceroute avanzado, huellas dactilares del sistema operativo remoto, adivinación del tiempo de actividad remoto, auditoría de pilas TCP/IP y otras funciones.==

**Comandos de Hping**

**Escaneo ACK en el puerto 80**  
**Ej.** **hping3 –A 10.0.0.25 –p 80** 
Para sondear la existencia de un cortafuegos y sus reglas.verifica si un host está activo en una red. ==**Si encuentra un host activo y un puerto abierto, devuelve una respuesta RST==

**Escaneo UDP en el puerto 80**  
**Ej.** **hping3 -2 10.0.0.25 –p 80**  
 ==Devuelve un mensaje ICMP de puerto inaccesible si encuentra el puerto cerrado y no devuelve ningún mensaje si el puerto está abierto.==
 
**Cortafuegos y marcas de tiempo**  
**Ej.** **hping3 -S 72.14.207.99 -p 80 --tcp-timestamp**
==Al agregar el argumento -S, puedes realizar un escaneo SYN.==

**Escaneo FIN, PUSH y URG en el puerto 80**  
**Ej.** **hping3 -F -P -U 10.0.0.25 -p 80**
==**realiza un escaneo de ping ICMP en toda la subred 10.0.1.x==

**Interceptar todo el tráfico que contiene la firma HTTP**  
**Ej.** **hping3 -9 HTTP -I eth0**El 
==**Argumento -9 configura Hping en modo de escucha**.==

**IP spoofing using Hping3:**
**Hping3 www.certifiedhacker.com -a 7.7.7.7**

**▪ Metasploit** 
**▪ NetScanTools Pro 

#### **Herramientas de Ping Sweep**  
▪ Angry IP Scanner
▪ SolarWinds Engineer’s Toolset  
▪ NetScanTools Pro 
▪ Colasoft Ping Tool 
▪ Advanced IP Scanner  
▪ OpUtils

==**Port Scanning Techniques**==

##### **TCP Connect/Full-Open Scan**
**nmap -sT -v 10.10.1.11**

**Stealth Scan (Half-Open Scan)** 
**nmap -sS -v 10.10.1.11**   

## Inverse TCP Flag Scan:
**Escaneo Xmas** : Escaneo TCP inverso con las banderas FIN, URG y PUSH 
 **nmap -sX -v 10.10.1.11** 
**(FIN) <br>nmap -sF -v 10.10.1.11;**     

**(Null) <br>nmap -sN -v 10.10.1.11** 
 ==Si el objetivo ha abierto el puerto, no recibirás ninguna respuesta. 
 Si el objetivo ha cerrado el puerto, recibirás una respuesta del sistema remoto con un RST==.  

**Escaneo TCP Maimon**
Similar al escaneo NULL, FIN y Xmas, pero **el paquete de sondeo utilizado aquí es FIN/ACK
nmap -sM -v 10.10.1.11
No response port open,  
RST packet    port  Close
IVMP unreacheble error port filtered

**ACK Flag Probe Scan** 
**nmap -sA -v 10.10.1.11**
No response Firewal Present
RST no firewal

**TTL-Based ACK Flag Probe scanning**
 nmap –ttl [time]
 ==Si el valor de TTL del paquete RST en un puerto en particular es menor que el valor límite de 64, entonces ese puerto está abierto.==

Window-Based ACK Flag Probe scanning**  
 **nmap -sW [tiempo]

==**IDLE/IPID Header Scan**==
==se puede utilizar para enviar una dirección de origen falsificada ==
**nmap -Pn -p- -sI 10.10.1.11 10.10.1.19**

**UDP Raw ICMP Port Unreachable Scanning**
**nmap -sU -v 10.10.1.11**
No response puerto Open
ICMP Unreacheble si el puerto esta Cerrado

**IPv6 Scan**
Scanning the IPv6 network 
**nmap -6 -v 10.10.1.11**

**Service Version Discovery**
**nmap -sV --reason -v -sT 10.10.1.11**

**-O** para realizar el descubrimiento del sistema operativo,
 **nmap -O** **10.10.1.11**

**OS Discovery using Nmap 

**nmap --script smb-os-discovery.nse 10.10.1.11**

 **nmap -6 -O** **10.10.1.11**

Scanning Beyond IDS and Firewall
**SYN/FIN Scanning Using IP Fragments**
**nmap -sS -T4 -A -f -v 10.10.1.11**

-f Opcion para fragmentar los packs
-A Agresive
-T4 nivel de velocidad del escaneo

**Source Port Manipulation**
nmap -g 80 10.10.1.11 
==-g especifica el puerto de origen==

 Decoy scans 
 ▪ **nmap -D RND:10 [target]** 
 **nmap -D RND: 10 10.10.1.11** 
 **nmap -D 192.168.0.1,172.120.2.8,192.168.2.8,10.10.1.19,10.10.1.5 10.10.1.11**
 
**Suplantación de dirección MAC (MAC Address Spoofing)**
**nmap -sT -Pn --spoof-mac 0 10.10.1.11**  (0 represents the randomization of the MAC address.**)

**▪ nmap -sT -Pn --spoof-mac [Vendor]
**nmap -sT -Pn --spoof-mac Dell 10.10.1.11**

**--spoof-mac [new MAC] represents manually setting the MAC address.**
**nmap -sT -Pn --spoof-mac 00:01:02:25:56:AE 10.10.1.11**  

**Creating Custom Packets**
**==Colasoft Packet Builder==**


| **Sistema Operativo** | **Time To Live (TTL)** | **Tamaño de Ventana TCP (TCP Window Size)** |
| --------------------- | ---------------------- | ------------------------------------------- |
| ==Linux==             | ==64==                 | ==5840==                                    |
| FreeBSD               | 64                     | 65535                                       |
| OpenBSD               | 255                    | 16384                                       |
| ==Windows==           | ==128==                | ==65,535 bytes a 1 Gigabyte==               |
| Cisco Routers         | 255                    | 4128                                        |
| Solaris               | 255                    | 8760                                        |
| AIX                   | 255                    | 16384                                       |

**Herramientas de Proxy (Proxy Tools)**
▪ **Proxy Switcher** 
**▪ CyberGhost VPN 


==NetBIOS Enumeration==

| **Código NetBIOS** | **Tipo** | **Descripción**                                                                                                                       |
| ------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <00>               | UNIQUE   | Nombre del **equipo (hostname)**. Indica el nombre de la máquina en la red.                                                           |
| <00>               | GROUP    | Nombre del **dominio o grupo de trabajo**. Identifica el dominio al que pertenece el equipo.                                          |
| <03>               | UNIQUE   | **Servicio de mensajería (Messenger Service)** asociado al **nombre del equipo**. Indica que el servicio está activo en la máquina.   |
| <03>               | UNIQUE   | **Servicio de mensajería asociado al usuario** (si hay una sesión iniciada).                                                          |
| ==<20>==           | UNIQUE   | ==**Servicio de servidor (Server Service)**. Indica que el equipo comparte recursos (archivos, impresoras, etc.).==                   |
| <1D>               | GROUP    | **Maestro navegador local (Master Browser)**. Identifica qué equipo actúa como "maestro" para listar dispositivos en la red (subred). |
| ==<1B>==           | UNIQUE   | ==**Controlador Principal de Dominio (PDC, Primary Domain Controller)**. Solo aparece en el PDC de un dominio Windows antiguo (NT).== |
| <1E>               | GROUP    | **Elecciones del servicio de navegación (Browser Elections)**. Usado en el proceso de selección del "maestro navegador".              |
==**Utilidad Nbtstat**==
```
nbtstat [-a <remotename>] [-A <IPaddress>] [-c] [-n] [-r] [-R] [-RR] [-s] [-S] [<interval>][-?]
```
Obtiene la table netbios de la maquina encuestada
“nbtstat –a  \<IP address of the remote machine\>" 

Obtiene el contenido del netbios name Cache
“nbtstat –c  \<IP address of the remote machine\>" 

**NetBIOS Enumeration Tools**
**▪ NetBIOS Enumerator**
==**▪ Nmap   nmap -sV -v --script nbstat.nse \<target IP address\>==

**Enumerating User Accounts** 
**PsTools** **▪ PsExec**  ▪ **PsFile**  ▪ **PsGetSid**  ▪ **PsKill**  

 Enumerating Shared Resources Using Net View 
 utilidad de línea de comandos que muestra una lista de computadoras en un grupo de trabajo especificado o los recursos compartidos disponibles

**net view**  **\\\\ \<computername\>**
**net view /domain:\<domain name\>** 

**Enumerating SNMP** 
SnmpWalk
snmpwalk -v1 -c public <Dirección IP del Objetivo>

==**Enumeración SNMP usando Nmap**==  
==**nmap -sU -p 161 --script=snmp-processes <Dirección IP del Objetivo>**==

**nmap -sU -p 161 --script=snmp-sysdescr <Dirección IP del Objetivo>** → Recupera información sobre el tipo de servidor SNMP y detalles del sistema operativo.

**nmap -sU -p 161 --script=snmp-win32-software <Dirección IP del Objetivo>** → Recupera una lista de todas las aplicaciones que se están ejecutando en la máquina objetivo

#### **SNMP Enumeration Tools**
 ▪ **snmp-check

LDAP Enumeration
**nmap -p 389 --script ldap.base='"cn=users,dc=CEH,dc=com ldap-brute "' \<Target IP Address\>**

#### **LDAP Enumeration Tools**
 **▪ Softerra LDAP Administrator**
 ##### **▪ ldapsearch**

==**NTP Enumeration**==

**ntpdate [-46bBdqsuv] [-a key] [-e authdelay] [-k keyfile] [-o version] [-p samples] [-t timeout] [ -U user_name] server [...]**

**ntptrace**

**NTP Enumeration Tools**
PRTG Network Monitor  
▪ Nmap
▪ udp-proto-scanner 
▪ NTP Server Scanne

**SMTP Enumeration using Nmap**
==**nmap -p 25, 365, 587 -script=smtp-commands \<Target IP Address \>**==

**nmap -p 25 -script=smtp-open-relay \<Target IP Address\>**

**nmap -p 25 –script=smtp-enum-users \<Target IP Address\>**

**SMTP Enumeration using Metasploit** 
msf > use auxiliary/scanner/smtp/smtp_enum 

#### **SMTP Enumeration Tools**
**▪ NetScanTools Pro;**  
**▪ smtp-user-enum**

**DNS Enumeration
dig ns \<dominio objetivo\>

**nslookup** 
**set querytype=soa** 
**\<target domain\>**
**ls -d \<domain of name server\>**

**▪ DNSRecon**
**dnsrecon -t axfr -d \<dominio objetivo\>

▪ Enumeración DNS usando OWASP Amass  

==**DNS and DNSSEC Enumeration using Nmap**==
**nmap --script=broadcast-dns-service-discovery \<Target Domain\>**
**nmap -T4 -p 53 --script dns-brute \<Target Domain\> Module**
**nmap -Pn -sU -p 53 --script=dns-recursion 192.168.1.150**

**nmap -sU -p 53 --script dns-nsec-enum --script-args dns-nsec-enum.domains= eccouncil.org \<target\>**


**Vulnerability Scoring Systems and Databases**

**Following are some of the vulnerability scoring systems and databases:**

▪ Common Vulnerability Scoring System (CVSS) 

▪ Common Vulnerabilities and Exposures (CVE) compartir información sobre una vulnerabilidad única de software o firmware.

▪ National Vulnerability Database (NVD) para los datos de gestión de vulnerabilidades basados en estándares.

▪ Common Weakness Enumeration (CWE) sistema de categorías para vulnerabilidades y debilidades en el software

==**Vulnerability Assessment Tools**==

**Nessus Essentials**
**GFI LanGuard**
**OpenVAS**
**Nikto**
**▪ Qualys Vulnerability Management 

==**Herramienta de Evaluación de Vulnerabilidades Impulsada por IA: **== 
- **CodeDefender**  
- Equixly
- **Corgea**  
- **Fluxguard** 