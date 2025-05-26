==Las herramientas de escaneo se utilizan para escanear e identificar hosts activos, puertos abiertos, servicios en ejecución en una red objetivo, información de ubicación, información de NetBIOS e información sobre todos los puertos TCP/IP y UDP abiertos.==

**Nmap** ("Network Mapper") es un escáner de seguridad para la exploración de redes y hacking. ==Permite descubrir hosts, puertos y servicios en una red informática, creando así un "mapa" de la red.==

**Syntax:** ``` # nmap <options> <Target IP address>```


**▪ Hping3**

==Es una herramienta orientada a la línea de comandos para el escaneo de redes y la creación de paquetes para el protocolo TCP/IP que envía solicitudes de eco ICMP y admite los protocolos TCP, UDP, ICMP y raw-IP. Realiza auditorías de seguridad de redes, pruebas de cortafuegos, descubrimiento manual de MTU de ruta, traceroute avanzado, huellas dactilares del sistema operativo remoto, adivinación del tiempo de actividad remoto, auditoría de pilas TCP/IP y otras funciones.==

**Puede enviar paquetes TCP/IP personalizados y mostrar las respuestas del objetivo de manera similar a un programa de ping con respuestas ICMP**. **Maneja la fragmentación así como el cuerpo y tamaño arbitrarios de los paquetes, y puede usarse para transferir archivos encapsulados bajo los protocolos admitidos. También admite el escaneo de hosts inactivos.** El **IP spoofing** y el escaneo de redes/hosts se pueden usar para realizar una exploración anónima de servicios.  También tiene un modo **Traceroute**, que permite a los atacantes enviar archivos entre canales encubiertos.

Syntax: # ```hping3 <options> <Target IP address>```

**Comandos de Hping**:  
**ICMP**  
**Ej.** **hping3 -1 10.0.0.25** Un barrido de ping o escaneo de Protocolo de Mensajes de Control de Internet (ICMP) es un proceso en el que se envía una solicitud ICMP o un ping a todos los hosts de la red para determinar cuáles están activos.

**Escaneo ACK en el puerto 80**  
**Ej.** **hping3 –A 10.0.0.25 –p 80** ==Esta técnica de escaneo puede usarse para sondear la existencia de un cortafuegos y sus reglas. Un filtrado simple de paquetes permite el establecimiento de una conexión (paquetes con el bit ACK activado),== mientras que un cortafuegos sofisticado basado en estado no permite el establecimiento de una conexión. ==Este escaneo se lleva a cabo cuando un host no responde a una solicitud de ping. Al emitir este comando, Hping verifica si un host está activo en una red. **Si encuentra un host activo y un puerto abierto, devuelve una respuesta RST**.==

**Escaneo UDP en el puerto 80**  
**Ej.** **hping3 -2 10.0.0.25 –p 80** Hping usa TCP como su protocolo predeterminado. Usar el argumento -2 en la línea de comandos especifica que Hping opera en modo UDP. Puedes usar tanto --udp como -2 como argumento en la línea de comandos. ==Hping envía paquetes UDP al puerto 80 del host (10.0.0.25). Devuelve un mensaje ICMP de puerto inaccesible si encuentra el puerto cerrado y no devuelve ningún mensaje si el puerto está abierto.==

**Recopilación del número de secuencia inicial**  
**Ej.** **hping3 192.168.1.103 -Q -p 139** ==Usando el argumento -Q en la línea de comandos, Hping recopila todos los números de secuencia TCP generados por el host objetivo (192.168.1.103).==

**Cortafuegos y marcas de tiempo**  
**Ej.** **hping3 -S 72.14.207.99 -p 80 --tcp-timestamp**

Muchos firewalls descartan esos paquetes TCP que no tienen la opción de marca de tiempo TCP establecida. Al agregar el argumento --tcp-timestamp en la línea de comandos, puedes habilitar la opción de marca de tiempo TCP en Hping y tratar de adivinar la frecuencia de actualización de la marca de tiempo y el tiempo de actividad del host de destino (72.14.207.99).

**Escaneo SYN en el puerto 50-60**  
**Ej.** **hping3 -8 50-60 -S 10.0.0.25 -V**  

==Usando el argumento -8 o --scan en la línea de comandos, estás operando Hping en modo escaneo para escanear un rango de puertos en el host de destino. Al agregar el argumento -S, puedes realizar un escaneo SYN.==

**Escaneo FIN, PUSH y URG en el puerto 80**  
**Ej.** **hping3 -F -P -U 10.0.0.25 -p 80** 

Al agregar los argumentos -F, -P y -U en la línea de comandos, estás configurando los paquetes FIN, PUSH y URG en los paquetes de sondeo. Al emitir este comando, realizas un escaneo FIN, PUSH y URG en el puerto 80 del host de destino (10.0.0.25). ==**Si el puerto 80 está abierto, no recibirás una respuesta.** **Si el puerto está cerrado, Hping devolverá una respuesta RST.**==

**Escanear toda la subred para encontrar hosts activos**  
**Ej.** **hping3 -1 10.0.1.x --rand-dest -I eth0**

==Al emitir este comando, Hping **realiza un escaneo de ping ICMP en toda la subred 10.0.1.x**; en otras palabras, envía una solicitud de eco ICMP aleatoriamente (--rand-dest) a todos los hosts desde 10.0.1.0 hasta 10.0.1.255 que están conectados a la interfaz eth0.== Los hosts cuyos puertos están abiertos responderán con una respuesta ICMP. En este caso, no has especificado un puerto; por lo tanto, Hping envía paquetes al puerto 0 en todas las direcciones IP de manera predeterminada.

**Interceptar todo el tráfico que contiene la firma HTTP**  
**Ej.** **hping3 -9 HTTP -I eth0**El 

==**Argumento -9 configura Hping en modo de escucha**.== Por lo tanto, al emitir el comando -9 HTTP, Hping comienza a escuchar en el puerto 0 (de todos los dispositivos conectados a la red a través de la interfaz eth0), intercepta todos los paquetes que contienen la firma HTTP y voltea el paquete desde el final de la firma hasta el final del paquete.

**SYN flooding a una víctima**  
**Ej.** **hping3 -S 192.168.1.1 -a 192.168.1.254 -p 22 --flood**

==El atacante emplea técnicas de SYN flooding TCP utilizando direcciones IP falsificadas para realizar un ataque DoS.==

**Metasploit**  
Fuente: [https://www.metasploit.com](https://www.metasploit.com)

==Metasploit es un proyecto de código abierto que proporciona la infraestructura, contenido y herramientas para realizar pruebas de penetración y auditorías de seguridad exhaustivas. Ofrece información sobre vulnerabilidades de seguridad y ayuda en la realización de pruebas de penetración y el desarrollo de firmas para sistemas de detección de intrusos (IDS). Facilita las tareas de los atacantes, escritores de exploits y escritores de payloads.==

Una de las principales ventajas del marco es su enfoque modular, es decir, permite la combinación de cualquier exploit con cualquier payload.
Metasploit permite automatizar el proceso de descubrimiento y explotación, proporcionando las herramientas necesarias para realizar la fase de pruebas manuales de una prueba de penetración. Modulos de escaneo

**▪ NetScanTools Pro 
Source:** https://www.netscantools.com
Es una herramienta de investigación que ==permite solucionar problemas, monitorear, descubrir y detectar dispositivos en su red. Usando esta herramienta, puede recopilar fácilmente información sobre la LAN local, así como sobre usuarios de Internet, direcciones IP, puertos==, etc. Los atacantes pueden encontrar vulnerabilidades y puertos expuestos en el sistema objetivo. Ayuda a los atacantes a listar direcciones IPv4/IPv6, nombres de host, nombres de dominio, direcciones de correo electrónico y URL de forma automática o manual (usando herramientas manuales). Combina muchas herramientas y utilidades de red categorizadas por sus funciones, como activas, pasivas, DNS y computadora local.

**Some additional scanning tools are listed below:** 
▪ sx (https://github.com) 
▪ RustScan (https://github.com) 
▪ MegaPing (http://magnetosoft.com) 
▪ SolarWinds®Engineer's Toolset (https://www.solarwinds.com) 
▪ PRTG Network Monitor (https://www.paessler.com)
