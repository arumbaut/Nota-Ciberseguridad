#### **▪ Information Gathering :
▪ who.is Source: https://who.is
The following are some additional information-gathering tools: 
▪ Whois Lookup (https://whois.domaintools.com) 
▪ Whois (https://www.whois.com) 
▪ Domain Dossier (https://centralops.net) 
▪ Subdomain Finder (https://pentest-tools.com)

Information Gathering a partir del archivo **==robots.txt==**

Un propietario de sitio web crea un archivo robots.txt para listar los archivos o directorios que un rastreador web debe indexar para proporcionar resultados de búsqueda. ==Los archivos robots.txt mal redactados pueden ocasionar la indexación completa de los archivos y directorios del sitio web. Si se indexan archivos y directorios confidenciales, un atacante puede obtener fácilmente información como contraseñas, direcciones de correo electrónico, enlaces ocultos y áreas de membresía==.

#### **▪Web Server Footprinting/Banner Grabbing**
**▪ Netcat
Source:**  https://netcat.sourceforge.net 
==Netcat es una utilidad de red que lee y escribe datos a través de conexiones de red utilizando el protocolo TCP/IP==. Es una ==herramienta de “back-end” confiable que se puede usar directamente o ser controlada por otros programas y scripts==. También es una herramienta de depuración y exploración de redes.
**Perform banner grabbing** 
**==nc –vv www. moviescope.com 80==** 

**▪ Telnet** 
**telnet www.moviescope.com 80**  Enter
==Type== 
#**GET / HTTP/1.0** Enter 2 veces

**▪ httprecon 
Source:** https://www.computec.ch 
Herramienta para la identificación avanzada de huellas de servidores web. Esta herramienta realiza ataques de captura de banner (banner-grabbing), enumeración de códigos de estado y análisis del orden de las cabeceras en el servidor web objetivo, y proporciona información precisa sobre el fingerprinting del servidor web.

**▪ Uniscan 
Source: https://sourceforge.net**
Herramienta versátil de fingerprinting de servidores que no solo ejecuta comandos simples como ping, traceroute y nslookup, sino que también realiza comprobaciones estáticas, dinámicas y de estrés en servidores web. ==Además de escanear sitios web, Uniscan realiza búsquedas automatizadas en Bing y Google para IPs específicas. **Compila todos estos datos en un informe completo**.==

==The following are some additional footprinting tools==: 
▪ Netcraft (https://www.netcraft.com)
▪ ID Serve (https://www.grc.com)
▪ Nmap (https://nmap.org)
▪ Ghost Eye (https://github.com)
▪ Skipfish (https://code.google.com)

**▪ Website Mirroring**

#### **▪ Vulnerability Scanning:**
**▪ Acunetix Web Vulnerability Scanner** 
**Source:** https://www.acunetix.com
==Analiza sitios web y detecta vulnerabilidades. Comprueba aplicaciones web en busca de inyecciones SQL, XSS, etc. Incluye herramientas avanzadas de pruebas de penetración para facilitar los procesos manuales de auditoría de seguridad y crea informes profesionales de auditoría de seguridad y cumplimiento normativo basados en la Tecnología AcuSensor.==
**▪ Nikto2**  
**Fuente:** [https://cirt.net](https://cirt.net)
Nikto es un escáner de vulnerabilidades ampliamente utilizado para identificar posibles vulnerabilidades en aplicaciones web y servidores web.

▪ OpenText Fortify WebInspect (https://www.opentext.com) 
▪ Tenable.io (https://www.tenable.com) 
▪ ImmuniWeb (https://www.immuniweb.com) 
**▪ Invicti** (https://www.invicti.com)

#### **▪ Session Hijacking:**
**BurpSuit https://portswigger.net**
Herramienta de pruebas de seguridad web que puede secuestrar identificadores de sesión (session IDs) en sesiones establecidas. La herramienta Sequencer de Burp Suite prueba la aleatoriedad de los tokens de sesión. Con esta herramienta, un atacante puede predecir el siguiente token de identificador de sesión posible y usarlo para apoderarse de una sesión válida.

▪ JHijack (https://sourceforge.net) ▪ Ettercap (https://www.ettercap-project.org)


**▪ Web Server Passwords Hacking:** 
**Hashcat https://hashcat.net**
 Hashcat es un descifrador compatible con múltiples sistemas operativos y plataformas, y puede realizar descifrado de contraseñas con múltiples hashes (MD4, MD5; SHA-224, 256, 384, 512; RIPEMD-160; etc.) en múltiples dispositivos. Los modos de ataque de esta herramienta son: directo, combinación, fuerza bruta, híbrido diccionario + máscara e híbrido máscara + diccionario.

 **▪ THC Hydra Source:** https://github.com
HC Hydra es un cracker de autenticación de inicio de sesión paralelizado que puede atacar numerosos protocolos

**▪ Ncrack (https://nmap.org)**
**▪ Rainbow crack (https://project-rainbowcrack.com)** 
**▪ Wfuzz (http://www.edge-security.com)**


