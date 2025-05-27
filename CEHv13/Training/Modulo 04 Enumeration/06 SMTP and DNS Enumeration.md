Los sistemas de correo comúnmente utilizan SMTP junto con POP3 e IMAP, lo que permite a los usuarios guardar mensajes en el buzón del servidor y descargarlos cuando sea necesario. SMTP utiliza servidores de intercambio de correo (MX) para dirigir el correo a través de DNS. Funciona en el puerto TCP 25, 2525 o 587.

▪ ==VRFY==: Validates users
$ telnet 192.168.168.1 25 
Trying 192.168.168.1... 
Connected to 192.168.168.1. 
Escape character is '^]'. 
220 NYmailserver ESMTP Sendmail 8.9.3 
HELO
501 HELO requires domain address 
HELO x
250 NYmailserver Hello [10.0.0.86], pleased to meet you 
VRFY Jonathan 
250 Super-User <Jonathan@NYmailserver> 
VRFY Smith
550 Smith... User unknown

▪ ==EXPN==: Displays the actual delivery addresses of aliases and mailing lists 
$ telnet 192.168.168.1 25 
Trying 192.168.168.1... 
Connected to 192.168.168.1. 
Escape character is '^]'. 
220 NYmailserver ESMTP Sendmail 8.9.3 
HELO
501 HELO requires domain address 
HELO x
250 NYmailserver Hello [10.0.0.86], pleased to meet you 
EXPN Jonathan 
250 Super-User <Jonathan@NYmailserver> 
EXPN Smith
550 Smith... User unknown 

▪ ==RCPT TO:== Defines the recipients of the message 
$ telnetl 192.168.168.1 25 
Trying 192.168.168.1 ... 
Connected to 192.168.168.1. 
Escape character is '^]'. 
220 NYmailserver ESMTP Sendmail 8.9.3 
HELO
501 HELO requires domain address 
HELO x
250 NYmailserver Hello [10.0.0.86], pleased to meet you 
MAIL FROM:Jonathan
250 Jonathan... Sender ok 
RCPT TO:Ryder
250 Ryder... Recipient ok 
RCPT TO: Smith 
550 Smith... User unknown


**SMTP Enumeration using Nmap**

SMTP provides the following three built-in commands:

**▪ VRFY: Validates users**

**▪ EXPN: Displays the actual delivery addresses of aliases and mailing lists**

**▪ RCPT TO: Defines the recipients of the message**

**SMTP Enumeration using Nmap**

▪ The following command, when executed, **lists all the SMTP commands available in the Nmap directory**:

**nmap -p 25, 365, 587 -script=smtp-commands \<Target IP Address \>**

▪ Run the following command to **identify SMTP open relays**:

**nmap -p 25 -script=smtp-open-relay \<Target IP Address\>**

▪ Run the following command to **enumerate all the mail users on the SMTP serve**r:

**nmap -p 25 –script=smtp-enum-users \<Target IP Address\>**

#### **SMTP Enumeration using Metasploit** 
El framework contiene un **módulo de enumeración SMTP** que permite a los atacantes conectarse al servidor SMTP objetivo y enumerar nombres de usuario usando listas de palabras predefinidas.  
El servidor SMTP utiliza su método incorporado **VRFY** para validar los nombres de usuario de la lista de palabras con los usuarios presentes en el servidor, y muestra la lista de usuarios que coinciden.

▪ Step 1: 
msf > use auxiliary/scanner/smtp/smtp_enum 
▪ Step 2: 
msf auxiliary(smtp_enum) > show options 
▪ Step 3: to set the target SMTP server’s IP address or a range of IP addresses.
msf auxiliary(smtp_enum) > set RHOST 
Step 4: 
msf auxiliary(smtp_enum) > set USER_FILE \<location of wordlists file\>
▪ Step 5: to view the complete list of available options in the SMTP user enumeration module
msf auxiliary(smtp_enum) >show advanced 
▪ Step 6: 
msf auxiliary(smtp_enum) >run 
#### **SMTP Enumeration Tools**

##### **▪ NetScanTools Pro;**  
**Fuente:** [https://www.netscantools.com](https://www.netscantools.com)  
**NetScanTools Pro** incluye una herramienta llamada **SMTP Email Generator**, que permite probar el proceso de envío de un mensaje de correo electrónico a través de un servidor SMTP.Los atacantes utilizan **NetScanTools Pro** para realizar **enumeración SMTP** y extraer todos los parámetros del encabezado del correo electrónico, incluyendo las banderas de confirmación/urgencia (_confirm/urgent flags_).

##### **▪ smtp-user-enum**

**Fuente:** [https://pentestmonkey.net](https://pentestmonkey.net)  
**smtp-user-enum** es una herramienta utilizada para **enumerar cuentas de usuario a nivel de sistema operativo** en **Solaris** a través del servicio SMTP (sendmail).
La enumeración se lleva a cabo **inspeccionando las respuestas** a los comandos **VRFY**, **EXPN** y **RCPT TO**.

smtp-user-enum.pl [opciones] (-u nombre_de_usuario | -U archivo_con_usuarios) (-t host | -T archivo_con_objetivos)


#### **DNS Enumeration using Zone Transfer** 

**Enumeración DNS usando Transferencia de Zona**La transferencia de zona DNS es el proceso de transferir una copia del archivo de zona DNS desde el servidor DNS primario a un servidor DNS secundario. En la mayoría de los casos, el servidor DNS primario mantiene un servidor de respaldo o secundario para redundancia, que contiene toda la información almacenada en el servidor primario. ==En la enumeración DNS mediante transferencia de zona, un atacante intenta recuperar una copia del archivo de zona completo para un dominio desde el servidor DNS. Los atacantes pueden realizar una transferencia de zona DNS usando herramientas como **nslookup, el comando dig y DNSRecon.**==

**▪ Comando dig:** 
dig ns \<dominio objetivo\>

**▪ Comando nslookup**
Los atacantes utilizan el comando **`nslookup`** en sistemas basados en Windows para **consultar servidores de nombres DNS** y **recuperar información** sobre:
- Direcciones de host del objetivo    
- Servidores de nombres (NS)    
- Intercambiadores de correo (MX)    
- Otros registros DNS

nslookup 
set querytype=soa 
\<target domain\>
ls -d \<domain of name server\>


**▪ DNSRecon**
Los atacantes utilizan DNSRecon para verificar todos los registros NS del dominio objetivo en busca de transferencias de zona.

**dnsrecon -t axfr -d \<dominio objetivo\>

En el comando anterior, la opción -t especifica el tipo de enumeración que se realizará, axfr es el tipo de enumeración en la que todos los servidores NS son probados para una transferencia de zona, y la opción -d especifica el dominio objetivo.

**DNS Cache Snooping**
El DNS cache snooping ==es un tipo de técnica de enumeración de DNS en la que un atacante consulta el servidor DNS para obtener un registro DNS específico almacenado en caché==. Al usar este registro en caché, el atacante puede determinar los sitios visitados recientemente por el usuario.

**▪ Non-recursive Method**

**dig @\<IP of DNS server\> \<Target domain\> A +norecurse**

**▪ Recursive Method**

**dig @\<IP of DNS server\> \<Target domain\> A +recurse**

#### **DNSSEC Zone Walking**
Las Extensiones de Seguridad del Sistema de Nombres de Dominio (DNSSEC) permiten proteger el DNS contra diversas amenazas mediante firmas digitales basadas en criptografía de clave pública. Estas firmas digitales se almacenan en los servidores de nombres DNS junto con registros comunes como MX, A, AAAA y CNAME.  
Sin embargo, ==**DNSSEC es vulnerable a un ataque llamado "zone walking"** o enumeración de zonas, un tipo de técnica de enumeración de DNS en la que un atacante intenta obtener registros internos si la zona DNS no está correctamente configurada.==

#### DNSSEC Zone Walking Tools
▪ **LDNS**  
Fuente: [https://www.nlnetlabs.nl](https://www.nlnetlabs.nl)
**LDNS-walk** enumera la zona **DNSSEC** y obtiene resultados sobre los archivos de registros DNS.

#### ▪ Enumeración DNS usando OWASP Amass  
**Fuente:** [https://github.com](https://github.com)

OWASP Amass es una herramienta de enumeración DNS que permite a los atacantes mapear la red objetivo y descubrir posibles superficies de ataque. Los atacantes usan una combinación de técnicas de reconocimiento **activo** y **pasivo** para recolectar información del DNS.

#### **DNS and DNSSEC Enumeration using Nmap**

Run the following command to ==list all the available services on the target host==:

**nmap --script=broadcast-dns-service-discovery \<Target Domain\>**

▪ Execute the following command ==to retrieve all the subdomains associated with the target host==:

**nmap -T4 -p 53 --script dns-brute \<Target Domain\> Module**

▪ Run the following command ==to check whether DNS recursion is enabled on the target server==:

**nmap -Pn -sU -p 53 --script=dns-recursion 192.168.1.150**

**DNS Security Extensions (DNSSEC) Enumeration using Nmap**

Attackers enumerate DNSSEC using dns-nsec-enum.nse or dns-nsec3-enum.nse NSE scripts to obtain information related to domains and their subdomains.
▪ Execute the following command to retrieve the list of subdomains associated with the target domain:

**nmap -sU -p 53 --script dns-nsec-enum --script-args dns-nsec-enum.domains= eccouncil.org \<target\>**

#### The following are some of the additional DNS enumeration tools: 
▪ Knock (https://github.com)
▪ Raccoon (https://github.com) 
▪ Subfinder (https://github.com) 
▪ Turbolist3r (https://github.com)

Otras Tecnicas de Enumeración 
**IPsec Enumeration**

**The following command can be used to perform an Nmap scan for checking the status of ISAKMP over port 500:**
**nmap –sU –p 500 \<target IP address\>**

**The following command is used for initial IPsec VPN discovery with ike-scan tool:**
ike-scan es una herramienta que permite descubrir hosts que ejecutan IKE (Internet Key Exchange) y realizar su identificación mediante patrones de retransmisión. ike-scan puede realizar las siguientes funciones:
- **Descubrimiento:** Detecta los hosts que ejecutan IKE en un rango de IPs mostrando aquellos que responden a las solicitudes IKE enviadas por ike-scan.    
- **Fingerprinting (Identificación):** Determina la implementación de IKE que usan los hosts y, en algunos casos, la versión del software que ejecutan. Esto se logra de dos formas:

**ike-scan –M \<target gateway IP address\>**

#### VoIP Enumeration 
VoIP (Voz sobre Protocolo de Internet) es una tecnología avanzada que ha reemplazado a la red telefónica conmutada pública tradicional (PSTN) tanto en entornos corporativos como domésticos.El Protocolo de Inicio de Sesión (SIP) es uno de los protocolos usados por VoIP para realizar llamadas de voz, videollamadas, etc., a través de una red IP. Este servicio SIP generalmente usa los puertos UDP/TCP 2000, 2001, 5060 y 5061.

**▪ Svmap**  
Fuente: [https://github.com](https://github.com)  
Svmap es un escáner de código abierto que identifica dispositivos SIP y servidores PBX en una red objetivo. Puede ser útil para los administradores de sistemas cuando se utiliza como una herramienta de inventario de red.

**svmap <target network range/IP Address>** 

#### **SMB Enumeration**

Server Message Block (SMB) es un protocolo de transporte que generalmente es utilizado por los sistemas Windows para proporcionar acceso compartido a archivos, impresoras y puertos serie, así como acceso remoto a los servicios de Windows. De manera predeterminada, SMB se ejecuta directamente en el puerto TCP 445 o a través de la API de NetBIOS en los puertos UDP 137 y 138, y los puertos TCP 137 y 139.

Comando de Nmap para enumerar el servicio SMB que se ejecuta en la dirección IP de destino:

**nmap -p 445 -A \<target IP\>**

Comandos de Nmap para enumerar los protocolos y versiones soportados del servidor SMB de destino:

**nmap -p 445 --script smb-protocols \<Target IP\>**

**nmap -p 139 --script smb-protocols \<Target IP\>**
