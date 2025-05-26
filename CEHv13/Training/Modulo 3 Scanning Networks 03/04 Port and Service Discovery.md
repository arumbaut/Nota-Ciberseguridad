El siguiente paso en el proceso de escaneo de redes consiste en verificar los puertos abiertos y los servicios en los sistemas activos. Este descubrimiento de puertos y servicios abiertos puede realizarse mediante varias técnicas de escaneo de puertos. Los administradores suelen utilizar estas técnicas para verificar las políticas de seguridad de sus redes, mientras que los atacantes las emplean para identificar puertos abiertos y servicios en ejecución en un host con la intención de comprometer la red.
#### **Port Scanning Techniques**

##### **TCP Connect/Full-Open Scan**

**El escaneo TCP** Connect/Full-Open es una de las formas más confiables de escaneo TCP. En el escaneo TCP Connect, la llamada al sistema connect() del sistema operativo intenta abrir una conexión a cada puerto de interés en la máquina objetivo. Si el puerto está escuchando, la llamada connect() resultará en una conexión exitosa con el host en ese puerto particular; de lo contrario, devolverá un mensaje de error indicando que el puerto no es alcanzable.  

| **nmap -sT -v 10.10.1.11**                              . | ![](attachments/image20250526110124.png) |
| --------------------------------------------------------- | ---------------------------------------- |


##### **Stealth Scan (Half-Open Scan)**  

El escaneo sigiloso implica restablecer la conexión TCP entre el cliente y el servidor de manera abrupta antes de completar la señalización del three-way handshake, lo que hace que la conexión quede a medio abrir. Este tipo de escaneo envía un solo paquete con la expectativa de una única respuesta. El escaneo a medio abrir abre parcialmente una conexión pero se detiene a mitad de camino.

**SYN Scan**

| **nmap -sS -v 10.10.1.11**                         . | ![](attachments/image20250526110302.png) |
| ---------------------------------------------------- | ---------------------------------------- |

##### **Inverse TCP Flag Scan:** 

==Los atacantes envían paquetes de sondeo TCP con una bandera TCP (FIN, URG, PSH) establecida o sin ninguna bandera. Cuando el puerto está abierto, el atacante no recibe ninguna respuesta del host, mientras que cuando el puerto está cerrado, recibe un RST del host objetivo.==

==Los mecanismos de seguridad, como los firewalls y los IDS, detectan los paquetes SYN enviados a los puertos sensibles de los hosts objetivo. Programas como Syslog están disponibles para registrar los intentos de escaneo con la bandera SYN a medio abrir. En algunos casos, los paquetes de sondeo habilitados con banderas TCP pueden pasar a través de los filtros sin ser detectados, dependiendo de los mecanismos de seguridad instalados.==
![](attachments/image20250526110623.png)

**Las configuraciones de bandera comunes utilizadas para un paquete de sondeo incluyen:**  
**▪ Un sondeo FIN** con la bandera TCP FIN establecida  
**▪ Un sondeo Xmas** con las banderas TCP FIN, URG y PUSH establecidas  
**▪ Un sondeo NULL** sin ninguna bandera TCP establecida  
**▪ Un sondeo SYN/ACK**

**Escaneo Xmas**

El escaneo **Xmas es un tipo de técnica de escaneo TCP inverso con las banderas FIN, URG y PUSH establecidas para enviar un marco TCP** a un dispositivo remoto. ==Si el objetivo ha abierto el puerto, no recibirás ninguna respuesta del sistema remoto. Si el objetivo ha cerrado el puerto, recibirás una respuesta del sistema remoto con un RST==.  

| **(Xmas) <br>nmap -sX -v 10.10.1.11**     | ![](attachments/image20250526111007.png) |
| ----------------------------------------- | ---------------------------------------- |
| **(FIN) <br>nmap -sF -v 10.10.1.11;**     |                                          |
| <br>**(Null) <br>nmap -sN -v 10.10.1.11** |                                          |

##### **Escaneo TCP Maimon**

==Esta técnica de escaneo es muy similar al escaneo NULL, FIN y Xmas, pero **el paquete de sondeo utilizado aquí es FIN/ACK**. En la mayoría de los casos, para determinar si el puerto está abierto o cerrado, el paquete RST debe generarse como respuesta a una solicitud de sondeo. Sin embargo, en muchos sistemas BSD, el puerto está abierto si el paquete es descartado en respuesta a un sondeo.==


| **nmap -sM -v 10.10.1.11** | ![](attachments/image20250526111351.png) |
| -------------------------- | ---------------------------------------- |


**ACK Flag Probe Scan**  
Los atacantes envían paquetes de sondeo TCP con la bandera **ACK** establecida a un dispositivo remoto y luego analizan la información del encabezado (TTL y campo WINDOW) de los paquetes **RST** recibidos para determinar si el puerto está abierto o cerrado. El escaneo de sonda con bandera ACK explota las vulnerabilidades dentro del **stack TCP/IP derivado de BSD**. ==Por lo tanto, este tipo de escaneo solo es efectivo en los sistemas operativos y plataformas en los que el stack TCP/IP se deriva de BSD.== 

| <br>**nmap -sA -v 10.10.1.11** | ![](attachments/image20250526111558.png) |
| ------------------------------ | ---------------------------------------- |
|                                | ![](attachments/image20250526111607.png) |


**TTL-Based ACK Flag Probe scanning**

En esta técnica de escaneo, primero necesitarás enviar paquetes de sondeo ACK (varios miles) a diferentes puertos TCP y luego analizar el valor del campo TTL de los paquetes RST recibidos. la sintaxis **nmap –ttl [time] [target]** se utiliza para realizar el escaneo basado en TTL. ==Si el valor de TTL del paquete RST en un puerto en particular es menor que el valor límite de 64, entonces ese puerto está abierto.==

**▪ Window-Based ACK Flag Probe scanning**  

En esta técnica de escaneo, primero necesitarás enviar paquetes de sondeo ACK (varios miles) a diferentes puertos TCP y luego analizar el valor del campo ventana de los paquetes RST recibidos. El usuario puede utilizar esta técnica de escaneo cuando todos los puertos devuelvan el mismo valor de TTL.

La opción **nmap -sW [tiempo] [objetivo]** se utiliza para realizar un escaneo basado en ventana. Si el valor de la ventana del paquete RST en un puerto en particular es diferente de cero, entonces ese puerto está abierto.

![](attachments/image20250526111952.png)


##### **IDLE/IPID Header Scan**

El escaneo de encabezado IDLE/IPID es un método de escaneo de puertos TCP que ==se puede utilizar para enviar una dirección de origen falsificada a una computadora y así determinar qué servicios están disponibles. Este método permite un escaneo completamente encubierto del host remoto. Un puerto se considera "abierto" si hay una aplicación que está escuchando en él. Una forma de comprobar si un puerto está abierto es enviando un paquete SYN (establecimiento de sesión) al puerto.== Si el puerto está abierto, la máquina objetivo responderá con un paquete SYN|ACK (confirmación de solicitud de sesión). Si el puerto está cerrado, responderá con un paquete RST (reset).

The attacker performs this scan by impersonating another computer via spoofing.

 In Zenmap, the **-sI** option is used to perform an IDLE scan.  
 
 **nmap -Pn -p- -sI 10.10.1.11 10.10.1.19**


##### **UDP Scan**

**UDP Raw ICMP Port Unreachable Scanning**

Los escáneres de puertos UDP utilizan el protocolo UDP en lugar de TCP. **No hay un handshake de tres vías para el escaneo UDP. El protocolo UDP puede ser más difícil de usar que el escaneo TCP porque se puede enviar un paquete pero no se puede determinar si el host está activo, inactivo o filtrado.** Sin embargo, se puede usar un paquete ICMP para verificar si los puertos están abiertos o cerrados. Si se envía un paquete UDP a un puerto sin una aplicación asociada a él, la pila IP devolverá un paquete ICMP de puerto inaccesible. Si cualquier puerto devuelve un error ICMP, estará cerrado, dejando los puertos que no respondieron como abiertos o filtrados por el firewall.

  

| **nmap -sU -v 10.10.1.11** | ![](attachments/image20250526120040.png) |
| -------------------------- | ---------------------------------------- |

**SCTP INIT Scan**

==SCTP se usa específicamente para realizar actividades de multi-homing y multi-streaming.Algunas aplicaciones de SCTP incluyen la detección de VoIP, telefonía IP y servicios relacionados con Signaling System 7 (SS7) / SIGnaling TRANsport (SIGTRAN)==

**nmap -sY -v 10.10.1.11**

**IPv6 Scan**
Scanning the IPv6 network is more difficult and complex compared to IPv4.

**nmap -6 -v 10.10.1.11**

##### **Service Version Discovery**

**nmap -sV --reason -v -sT 10.10.1.11**

▪ Omitir pruebas no críticas  
Evitar un escaneo intensivo si solo se requiere una cantidad mínima de información.  
o El número de puertos escaneados puede limitarse utilizando comandos específicos.  
o El escaneo de puertos (-sn) puede omitirse si y solo si se desea verificar si los hosts están en línea o no.  
o Se pueden evitar tipos de escaneo avanzados (-sC, -sV, -O, --traceroute y -A) **-sn — Ping Scan (sin escaneo de puertos); -sC — Ejecutar scripts NSE predeterminados; -sV — Detección de versión; -O — Detección de sistema operativo; --traceroute — Trazado de ruta; -A — Escaneo agresivo; -n — No realizar resolución DNS**.  
o La resolución DNS debe activarse solo cuando sea necesario.  
▪ Optimizar los parámetros de tiempo  
Para controlar la actividad del escaneo, Nmap proporciona la opción -T para escanear con niveles de agresividad de tiempo que van desde bajo a alto. **(T0...T5)**