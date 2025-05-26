**Descubrimiento del Sistema Operativo / Banner Grabbing**
El banner grabbing, o "huella digital del sistema operativo" (OS fingerprinting), es un método utilizado para determinar el sistema operativo que se está ejecutando en un sistema objetivo remoto.

Dos tipos de técnicas de banner grabbing  
**▪ Banner Grabbing Activo**
==El banner grabbing activo aplica el principio de que la pila IP de un sistema operativo responde de manera única a paquetes TCP especialmente diseñados==. Esto ocurre debido a las diferentes interpretaciones que los proveedores aplican al implementar la pila TCP/IP en un sistema operativo determinado. **En el banner grabbing activo, el atacante envía una variedad de paquetes malformados al host remoto y compara las respuestas con una base de datos. Las respuestas de los diferentes sistemas operativos varían debido a las diferencias en la implementación de la pila TCP/IP.**

**▪ Banner Grabbing Pasivo**
Fuente: [https://www.broadcom.com](https://www.broadcom.com)  
Al igual que el banner grabbing activo, el banner grabbing pasivo también depende de la implementación diferencial de la pila y de las distintas formas en que un sistema operativo responde a los paquetes. Sin embargo, en lugar de depender del escaneo del host objetivo, la toma de huellas pasiva captura paquetes del host objetivo mediante el sniffing para estudiar señales reveladoras que puedan revelar un sistema operativo.  
**El banner grabbing pasivo incluye:**  

**Banner grabbing from error messages**: **Los mensajes de error proporcionan información, como el tipo de servidor, tipo de sistema operativo y herramientas SSL utilizadas por el sistema remoto objetivo.**

**Sniffing the network traffic:** **Capturar y analizar paquetes del objetivo permite al atacante determinar el sistema operativo utilizado por el sistema remoto.**

**Banner grabbing from page extensions****:
**Buscar una extensión en la URL puede ayudar a determinar la versión de la aplicación. Por ejemplo, .aspx indica un servidor IIS y una plataforma Windows.**

==El campo TTL (Time to Live) determina el tiempo máximo que un paquete puede permanecer en una red, y el tamaño de la ventana TCP determina la longitud del paquete reportado. Estos valores varían entre los sistemas operativos, como se describe en la siguiente tabla==.

![](attachments/image20250526120942.png)

##### **OS Discovery using Wireshark** 
Source: https://www.wireshark.org 
Para identificar el sistema operativo del objetivo, se debe interceptar/capturar la respuesta generada por la máquina objetivo hacia la máquina que originó la solicitud, utilizando herramientas de captura de paquetes como Wireshark, entre otras, y observar los campos TTL y tamaño de ventana TCP en el primer paquete TCP capturado. Al comparar estos valores con los de la tabla anterior, se puede determinar el sistema operativo del objetivo que generó la respuesta.

##### **OS Discovery using Nmap and Unicornscan** 

En map, se utiliza la opción **-O** para realizar el descubrimiento del sistema operativo, lo cual muestra los detalles del sistema operativo de la máquina objetivo.
 
 **nmap -O** **10.10.1.11**

**OS Discovery using Unicornscan** 
Source: https://sourceforge.net 

En Unicornscan, el sistema operativo de la máquina objetivo puede identificarse observando los valores de TTL en el resultado obtenido del escaneo. Para realizar un escaneo con Unicornscan, se utiliza la sintaxis **`#unicornscan <dirección IP del objetivo>`**. Como se muestra en la captura de pantalla, el valor de TTL obtenido después del escaneo es 128; por lo tanto, el sistema operativo es posiblemente **Microsoft Windows**.

 **`unicornscan 10.10.1.22 -Iv`**


**OS Discovery using Nmap Script Engine**

El Nmap Scripting Engine (NSE) en Nmap se puede utilizar para automatizar una amplia variedad de tareas de red, permitiendo a los usuarios escribir y compartir scripts. Por ejemplo, en **Nmap, smb-os-discovery es un script integrado utilizado para recopilar información del sistema operativo en la máquina objetivo a través del protocolo SMB**. Si se desean especificar scripts personalizados, los atacantes pueden usar la opción --script.

**nmap --script smb-os-discovery.nse 10.10.1.11**

**OS Discovery using IPv6 Fingerprinting**

 **nmap -6 -O** **10.10.1.11**