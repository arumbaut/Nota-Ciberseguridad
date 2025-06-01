**Types of Privilege Escalation**

▪ **Horizontal Privilege Escalation:** En una escalada horizontal de privilegios, el usuario no autorizado intenta acceder a los recursos, funciones y otros privilegios que pertenecen a un usuario autorizado que tiene permisos de acceso similares. Por ejemplo, el usuario A de la banca en línea puede acceder fácilmente a la cuenta bancaria del usuario B.

▪ **Vertical Privilege Escalation:** En una escalada vertical de privilegios, un usuario no autorizado intenta obtener acceso a los recursos y funciones de un usuario con privilegios más altos, como administradores de aplicaciones o del sitio. Por ejemplo, alguien que utiliza la banca en línea puede acceder al sitio utilizando funciones administrativas.

#### **Privilege Escalation Using DLL Hijacking**
Los atacantes utilizan herramientas como Spartacus, DLLirant, ImpulsiveDLLHijack y PowerSploit para detectar DLLs susceptibles a secuestro y llevar a cabo el secuestro de DLL en el sistema objetivo.

**Attackers use tools such as** 
**Spartacus,** 
**DLLirant,**
**ImpulsiveDLLHijack,** 
**PowerSploit** 
to detect hijackable DLLs and perform DLL hijacking on the target system: 
#### **Privilege Escalation Using Dylib Hijacking (Ataques a Bibliotecas Dinámicas en macOS)**
El ataque con bibliotecas dinámicas en macOS es similar al DLL Hijacking en Windows, donde un atacante logra ejecutar código malicioso al engañar al sistema para que cargue una biblioteca falsa en lugar de una legitima

**Privilege Escalation Using Spectre and Meltdown Vulnerabilities**


==**Spectre y Meltdown** son vulnerabilidades descubiertas en el diseño de procesadores modernos de fabricantes como **AMD, ARM e Intel**==. Estas fallas se deben a optimizaciones de rendimiento implementadas en los procesadores para hacer que las computadoras sean más rápidas.

**Spectre Vulnerability**
Esta falla permite a los atacantes engañar al procesador para que utilice la ejecución especulativa y acceda a datos restringidos.Afecta a muchos procesadores modernos, incluidos los de **Apple, AMD, ARM, Intel, Samsung y Qualcomm.**

**Meltdown Vulnerability**
Esta vulnerabilidad permite a los atacantes forzar un proceso para que acceda a memoria fuera de sus límites al explotar mecanismos de optimización de CPU, como la ejecución especulativa

**Privilege Escalation Using Named Pipe Impersonation (Suplantación de Named Pipes)**
Las Named Pipes son un mecanismo que Windows utiliza para permitir que diferentes programas o procesos se comuniquen entre sí. Piensa en ellas como un canal privado de comunicación entre dos aplicaciones.

#### **Privilege Escalation by Exploiting Misconfigured Services**

##### ¿Qué son los servicios mal configurados?
 Windows y otros sistemas operativos ejecutan servicios en segundo plano para diversas tareas. Si estos servicios no están bien configurados, un atacante puede manipularlos para obtener más permisos dentro del sistema.

**Pivoting and Relaying to Hack External Machines** **(****Pivoting y Relaying para Hackear Máquinas Externas****)**

Son técnicas utilizadas por los atacantes para obtener información detallada sobre una red objetivo. Estas técnicas se ejecutan después de comprometer con éxito un sistema dentro de la red.

El sistema comprometido se usa como un punto de acceso para penetrar más profundamente en la red y acceder a otros sistemas y recursos que normalmente serían inaccesibles desde la red del atacante.

**Pivoting: Solo se explotan los sistemas accesibles a través del sistema comprometido.**

==**Pivoting: Permite a los atacantes abrir una shell remota en otro sistema, pero a través de la sesión inicial en el sistema comprometido.**==

**Relaying: Se accede a los recursos disponibles en otros sistemas a través del sistema comprometido.**

==**Relaying: Permite a los atacantes acceder a recursos internos (archivos, servidores, bases de datos) utilizando una sesión shell tunelada en el sistema comprometido.**==

**En este caso, el atacante no solo usa el sistema comprometido como trampolín, sino que también accede a los recursos internos sin necesidad de comprometer cada sistema individualmente.**

#### Privilege Escalation Using Misconfigured NFS 
**¿Qué es NFS?**

NFS (Network File System) es un protocolo que permite que los dispositivos (como servidores y computadoras) compartan archivos entre sí dentro de una red interna (intranet). Este protocolo es muy utilizado en redes de empresas donde se necesitan compartir archivos entre distintos equipos de manera eficiente.
#### ¿Cómo Funciona NFS?
NFS usa puerto 2049 para que el servidor y el cliente se comuniquen.

Para que el cliente pueda acceder a los archivos del servidor, se emplea un protocolo llamado Remote Procedure Call (RPC), que le permite ejecutar procedimientos de forma

Una mala configuración en NFS abre la puerta para que los atacantes obtengan acceso a nivel de root a través de una cuenta de usuario común o de bajo privilegio.

**Privilege Escalation by Bypassing User Account Control (UAC)**

Cuando los atacantes no logran **escalar privilegios** utilizando un **payload** sencillo, intentan **evadir las características de seguridad de Windows**, como el **Control de Cuentas de Usuario (UAC)****.**Alternativamente, los atacantes pueden **inyectar malware en un proceso de confianza** para obtener privilegios elevados sin ninguna notificación al usuario.

#### ¿Qué es el Control de Cuentas de Usuario (UAC)?

El Control de Cuentas de Usuario (UAC) es una característica de seguridad en Windows diseñada para evitar que programas maliciosos realicen cambios no autorizados en el sistema. Cuando un programa intenta hacer algo que requiere privilegios elevados (como modificar configuraciones del sistema o instalar software), el UAC solicita permiso al usuario antes de proceder.

**Privilege Escalation Tools**

**▪ BeRoot** is a post-exploitation tool to check common misconfigurations to find a way to escalate privilege.

**▪ pwncat** allows attackers to locate and exploit vulnerabilities associated with user accounts and session for privilege escalation.

**==pwncat$ escalate list -u root==**

**Some additional privilege escalation tools are listed as follows:** 
▪ PowerSploit (https://github.com) 
▪ Traitor (https://github.com)
▪ PEASS-ng (https://github.com) 
▪ FullPowers (https://github.com)
