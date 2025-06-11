Scanning Tools

**Nmap** 
Notas importantes parametros
Opción -F mayuscula : escanea solo los 100 puesrtos mas comunes
-p- : escanea los 65535 puertos 
Puertos conocidos: desde el  0  al  1023  
Puertos Registrados : desde el 1024  al  49.151, 
Puertos dinámicos  o  privados: desde el 49.152  al  65.535]
Opción -f minudcula : Frangmnta paquetes


**Escaneo ARP Ping**.
 **nmap -sn -PR target.** 
**-sn** es el comando de Nmap que **se utiliza para deshabilitar el escaneo de puertos**

**Escaneo UDP Ping**.
**nmap -sn -PU target**

**Escaneo ICMP ECHO Ping**
**nmap -sn -PE target**

 **ICMP ECHO Ping Sweep (también conocido como barrido ICMP) ** 
**nmap -sn -PE** **target** **10.10.1.5-24**

**Escaneo ICMP Timestamp Ping.**
**nmap -sn -PM** **target** **10.10.1.5**


 **TCP SYN Ping Scan** 
**nmap -sn -PS 10.10.1.5**
 El TCP SYN ping es una técnica de descubrimiento de hosts que se utiliza para sondear diferentes puertos y determinar si están en línea, así como para identificar si existen reglas de firewall activas. 

**TCP ACK Ping Scan**
 **La recepción del paquete RST por parte del atacante indica que el host está activo
**nmap -sn -PA 10.10.1.5**

**IP Protocol Ping Scan**
**nmap -sn -PO 10.10.1.5**

**▪ Hping3**
 Es una herramienta orientada a la línea de comandos para el escaneo de redes y la creación de paquetes para el protocolo TCP/IP que envía solicitudes de eco ICMP y admite los protocolos TCP, UDP, ICMP y raw-IP. Realiza auditorías de seguridad de redes, pruebas de cortafuegos, descubrimiento manual de MTU de ruta, traceroute avanzado, huellas dactilares del sistema operativo remoto, adivinación del tiempo de actividad remoto, auditoría de pilas TCP/IP y otras funciones. 

**Comandos de Hping**

**Escaneo ACK en el puerto 80**  
**hping3 –A 10.0.0.25 –p 80** 
Para sondear la existencia de un cortafuegos y sus reglas.verifica si un host está activo en una red.  **Si encuentra un host activo y un puerto abierto, devuelve una respuesta RST 

**Escaneo UDP en el puerto 80**  
**Ej.** **hping3 -2 10.0.0.25 –p 80**  
  Devuelve un mensaje ICMP de puerto inaccesible si encuentra el puerto cerrado y no devuelve ningún mensaje si el puerto está abierto. 
 
**Cortafuegos y marcas de tiempo**  
**Ej.** **hping3 -S 72.14.207.99 -p 80 --tcp-timestamp**
 Al agregar el argumento -S, puedes realizar un escaneo SYN. 

**Escaneo FIN, PUSH y URG en el puerto 80**  
**Ej.** **hping3 -F -P -U 10.0.0.25 -p 80**
 **realiza un escaneo de ping ICMP en toda la subred 10.0.1.x 

**Interceptar todo el tráfico que contiene la firma HTTP**  
**Ej.** **hping3 -9 HTTP -I eth0**El 
 **Argumento -9 configura Hping en modo de escucha**. 


 **Port Scanning Techniques** 

##### **TCP Connect/Full-Open Scan**
**nmap -sT -v 10.10.1.11**

**Stealth Scan (Half-Open Scan)** 
**nmap -sS -v 10.10.1.11**   

## Inverse TCP Flag Scan:
**Escaneo Xmas** : Escaneo TCP inverso con las banderas FIN, URG y PUSH 
 **nmap -sX -v 10.10.1.11** 
**(FIN) <br>nmap -sF -v 10.10.1.11;**     

**(Null) <br>nmap -sN -v 10.10.1.11** 
  Si el objetivo ha abierto el puerto, no recibirás ninguna respuesta. 
 Si el objetivo ha cerrado el puerto, recibirás una respuesta del sistema remoto con un RST .  

**Escaneo TCP Maimon**
Similar al escaneo NULL, FIN y Xmas, pero **el paquete de sondeo utilizado aquí es FIN/ACK
nmap -sM -v 10.10.1.11
No responde  puerto abierto,  
RST packet    puerto cerrado
ICMP unreacheble error puerto filtrado

**ACK Flag Probe Scan** 
**nmap -sA -v 10.10.1.11**
No response Firewal Present
RST no firewal

**TTL-Based ACK Flag Probe scanning**
 nmap –ttl [time]
  Si el valor de TTL del paquete RST en un puerto en particular es menor que el valor límite de 64, entonces ese puerto está abierto. 

Window-Based ACK Flag Probe scanning**  
 **nmap -sW [tiempo]

 **IDLE/IPID Header Scan** 
 se puede utilizar para enviar una dirección de origen falsificada  
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
 -g especifica el puerto de origen 

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
** Colasoft Packet Builder