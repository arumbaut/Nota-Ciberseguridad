Después de ejecutar aplicaciones maliciosas en un sistema objetivo y obtener privilegios elevados, los atacantes ocultan sus programas para evitar su detección y eliminación. Para ello, emplean diversas técnicas como rootkits, flujos de datos alternativos de NTFS (NTFS streams) y esteganografía.

**Rootkits**

Los rootkits son programas maliciosos diseñados para obtener acceso a un sistema sin ser detectados. Su objetivo principal es otorgar privilegios de root a un atacante, lo que le permite realizar diversas acciones maliciosas, como instalar software no autorizado, eliminar archivos y modificar configuraciones del sistema.

#### **Cómo Funcionan los Rootkits**

Explotan vulnerabilidades en el sistema operativo y sus aplicaciones.

Crean un proceso de inicio de sesión encubierto (backdoor) que permite al atacante eludir los mecanismos de autenticación estándar.

Ocultan rastros de acceso no autorizado mediante la manipulación de controladores o módulos del núcleo (kernel).

Sustituyen llamadas del sistema operativo y utilidades con versiones modificadas que ejecutan funciones maliciosas.

**Componentes Comunes de un Rootkit**  

Programas backdoor para acceso remoto persistente.

Herramientas para ataques de denegación de servicio distribuido (DDoS).

Sniffers de paquetes para capturar información de red.

Utilidades para eliminar registros de actividad (log-wiping).

Bots de IRC para control remoto y comunicación con servidores maliciosos.

  
**Types of Rootkits**

**▪ Hypervisor-Level Rootkit:** Attackers create hypervisor-level rootkits by exploiting hardware features such as Intel VT and AMD-V

**▪ Hardware/Firmware Rootkit:** Hardware/firmware rootkits use devices or platform firmware to create a persistent malware image in hardware, such as a hard drive, system BIOS, or network card.

**▪ Kernel-Level Rootkit:** The kernel is the core of an OS. A kernel-level rootkit runs in Ring-0 with the highest OS privileges.

**▪ Boot-Loader-Level Rootkit:** Boot-loader-level rootkits (**bootkits**) function either by modifying the legitimate boot loader or replacing it with another one. The bootkit can activate even before the OS starts.

**▪ Application-Level/User-Mode Rootkit:** An application-level/user-mode rootkit runs in Ring-3 as a user along with other applications in the system. It exploits the standard behavior of APIs.

### **Cómo Funciona un Rootkit**

Un rootkit opera incrustándose profundamente en el sistema para evadir la detección y mantener acceso persistente. Una de las técnicas principales que utiliza es el **system hooking**

**Creación de la Línea Base:**
Se ejecutan herramientas como **Tripwire y AIDE** en un sistema limpio.
 Estas herramientas generan un registro de referencia de los archivos del sistema, registros de arranque (boot records) y la memoria

#### Popular Rootkits 
**▪ FudModule Rootkit** 
**▪ Fire Chili Rootkit** 
**▪ CopperStealer** 
**▪ Syslogk** 
**▪ Stealthy Universal Rootkit** 
**▪ Reptile rootkit** 
**▪ CosmicStrand**

**Steps for Detecting Rootkits**

**Manually examine the filesystem and registry of the system to detect rootkits**

  

![](file:///C:\Users\adrian\AppData\Local\Temp\ksohtml9668\wps1.jpg) 

![](file:///C:\Users\adrian\AppData\Local\Temp\ksohtml9668\wps2.jpg) 

#### Anti-Rootkits 
▪ GMER Source: http://www.gmer.net 
GMER es una aplicación que ayuda a los profesionales de seguridad a detectar y eliminar rootkits mediante el escaneo de procesos, hilos, módulos, servicios, archivos, sectores del disco (MBR), ADSs, claves del registro, hooks de controladores – SSDT, IDT, llamadas IRP y hooks en línea.

▪ Stinger (https://www.trellix.com)
▪ Avast One (https://www.avast.com)
▪ TDSSKiller (https://usa.kaspersky.com)
▪ Malwarebytes Anti-Rootkit (https://www.malwarebytes.com)
▪ AVG Rootkit Scanner (https://www.avg.com)


**NTFS Data Stream**

NTFS (New Technology File System) es un sistema de archivos utilizado en sistemas operativos Windows para almacenar y organizar los archivos en un disco duro o dispositivo de almacenamiento. NTFS almacena los archivos mediante el uso de flujos de datos (data streams) y atributos de archivos

![](attachments/image20250527131511.png)

![](attachments/image20250527131605.png)

#### NTFS Stream Detectors
**▪ Stream Armor Source: https://securityxploded.com** 
**▪ Stream Detector (https://www.novirusthanks.org)** 
**▪ GMER (http://www.gmer.net)** 
**▪ ADS Scanner (https://www.pointstone.com)**
**▪ Streams (https://learn.microsoft.com)** 
**▪ AlternateStreamView (https://www.nirsoft.net)**
