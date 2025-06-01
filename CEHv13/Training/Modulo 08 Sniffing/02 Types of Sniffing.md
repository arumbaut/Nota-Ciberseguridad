#### **El sniffing activo**

==El **sniffing pasivo** no implica el envío de paquetes. Simplemente captura y monitorea los paquetes que fluyen en la red. Un sniffer de paquetes por sí solo no es preferido para un ataque porque solo funciona en un dominio de colisión común==. Un dominio de colisión común es el sector de la red que no está conmutado ni puenteado (es decir, conectado a través de un hub).

##### Los atacantes utilizan los siguientes métodos de sniffing pasivo para obtener control sobre una red objetivo:

**▪ Compromiso de la seguridad física**

**▪ Uso de un caballo de Troya: La mayoría de los troyanos tienen capacidad de sniffing integrada.**

##### **Sniffing Activo**
==El **sniffing activo** busca tráfico en una LAN conmutada mediante la inyección activa de tráfico en ella. El sniffing activo también se refiere al sniffing a través de un switch. En el sniffing activo, el Ethernet conmutado no transmite información a todos los sistemas conectados a través de la LAN como lo haría en una red basada en un hub. Los switches mantienen su propia caché ARP en Memoria de Direccionamiento Contenidos (CAM). CAM es un tipo especial de memoria que mantiene un registro de qué host está conectado a qué puerto.==

Para resumir los tipos de sniffing: ==el sniffing pasivo no envía ningún paquete; solo monitorea los paquetes enviados por otros. El sniffing activo implica enviar múltiples sondeos de red para identificar puntos de acceso.==

##### The following is a list of different active sniffing techniques:
**▪ MAC flooding**
**▪ DNS poisoning**
**▪ ARP poisoning**
**▪ DHCP attacks**
**▪ Switch port stealing**
**▪ Spoofing attack**

**Protocols Vulnerable to Sniffing**

**▪ Telnet and Rlogin**
**▪ HTTP**
**▪ SNMP**
**▪ SMTP**
**▪ NNTP**
**▪ POP**
**▪ FTP**
**▪ IMAP**
**▪ TFTP**

**Sniffing en la Capa de Enlace de Datos del Modelo OSI**
El modelo OSI describe las funciones de la red como una serie de siete capas. Cada capa proporciona servicios a la capa superior y recibe servicios de la capa inferior. La capa de enlace de datos es la segunda capa del modelo OSI. En esta capa, los paquetes de datos se codifican y decodifican en bits. Los sniffers operan en la capa de enlace de datos y pueden capturar paquetes de esta capa. Las capas de red en el modelo OSI están diseñadas para funcionar independientemente unas de otras; por lo tanto, si un sniffer esnifa datos en la capa de enlace de datos, las capas superiores del modelo OSI no serán conscientes del sniffing.

**Analizador de Protocolo**

==Un analizador de protocolo de hardware es un dispositivo que interpreta el tráfico que pasa por una red. Captura señales sin alterar el segmento de tráfico. Su propósito es monitorear el uso de la red e identificar el tráfico malicioso generado por software de hacking instalado en la red. Captura un paquete de datos, lo decodifica y analiza su contenido según reglas predeterminadas. Permite a un atacante ver los bytes individuales de datos de cada paquete que pasa por la red.==

En comparación con los analizadores de protocolo de software, los analizadores de protocolo de hardware son capaces de capturar más datos sin pérdida de paquetes en el momento de sobrecarga de datos.

##### Hardware protocol analyzers from different manufacturers include the following.

  ▪ Xgig 1000 32/128 G FC & 25/50/100 GE Analyzer
▪ SierraNet M1288 Source: https://www.teledynelecroy.com
▪ PTW60 (https://www.globalspec.com)
▪ P5551A PCIe 5.0 Protocol Exerciser (https://www.keysight.com)
▪ Voyager M4x (https://www.teledynelecroy.com)
▪ N2X N5540A Agilent Protocol Analyzer (https://www.valuetronics.com)
▪ Xgig 16-Lane PCI Express 4.0 Chassis (https://www.viavisolutions.com)

**Puerto SPAN**
==El Switched Port Analyzer (SPAN) es una característica de los switches Cisco, también conocida como "duplicación de puertos" (port mirroring), que monitorea el tráfico de red en uno o más puertos del switch. Un puerto SPAN es un puerto configurado para recibir una copia de cada paquete que pasa por un switch.== Ayuda a analizar y depurar datos, identificar errores e investigar accesos no autorizados a la red.

**Wiretapping, or telephone tapping**

L==a intercepción de comunicaciones o escucha telefónica se refiere a la vigilancia de conversaciones telefónicas o de Internet por parte de un tercero con intenciones encubiertas. Para realizar la intercepción, el atacante primero selecciona a una persona o host objetivo en la red para espiar y luego conecta un dispositivo de escucha (hardware, software o una combinación de ambos) al circuito que transporta la información entre los dos teléfonos o hosts objetivo.==

**Wiretapping Methods :**
 ▪ The official tapping of telephone lines
▪ The unofficial tapping of telephone lines
▪ Recording the conversation
▪ Direct line wiretap
▪ Radio wiretap

**Types of Wiretapping:**

**▪ Active Wiretapping :** La intercepción activa es un ataque MITM (Man-in-the-Middle). Esto permite a un atacante monitorear y grabar el tráfico o el flujo de datos en un sistema de comunicación. El atacante también puede alterar o inyectar datos en la comunicación o el tráfico.

**▪ Passive Wiretapping :** La intercepción pasiva es el esnifado o la escucha. Esto permite a un atacante monitorear y grabar el tráfico. Al observar el flujo de tráfico grabado, el atacante puede espiar contraseñas u otra información.

**Lawful Interception**

La intercepción legal (LI, por sus siglas en inglés) se refiere a la interceptación legal de la comunicación de datos entre dos puntos finales para la vigilancia en redes tradicionales de telecomunicaciones, VoIP, datos y redes multiservicio. La LI obtiene datos de una red de comunicación para su análisis o como evidencia. Esto es útil en actividades como la gestión y protección de infraestructuras, así como en cuestiones relacionadas con la ciberseguridad.