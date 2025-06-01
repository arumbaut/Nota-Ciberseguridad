os atacantes se enfocan especialmente en el secuestro de sesiones a nivel de red porque no requiere acceso al host, ni la necesidad de personalizar sus ataques para cada aplicación, a diferencia del secuestro a nivel de aplicación

#### **The following are different types of network-level hijacking:**
**▪ Blind hijacking**
**▪ UDP hijacking**
**▪ TCP/IP hijacking**
**▪ RST hijacking**
**▪ Man-in-the-middle: packet sniffer**
**▪ IP spoofing: source routed packets**

**TCP/IP Hijacking** **:** ==Un atacante intercepta una conexión establecida entre dos partes que se comunican, utilizando paquetes falsificados y luego finge ser una de esas partes.== En este enfoque, ==el atacante usa paquetes falsificados para redirigir el tráfico TCP a su propia máquina. Una vez que esto es exitoso, la conexión del víctima se interrumpe, y el atacante puede comunicarse con la máquina del host en nombre de la víctima.== ==Para llevar a cabo un ataque de secuestro de TCP/IP, tanto la víctima como el atacante deben estar en la misma red==. El servidor objetivo y las máquinas de la víctima pueden estar ubicadas en cualquier lugar.Si el atacante envía los datos con el número de secuencia esperado antes de que el usuario lo haga, el servidor se sincronizaría con el atacante. Esto llevaría a la establecimiento de una conexión entre el atacante y el servidor. Luego, el servidor descartaría los datos enviados por el usuario con el número de secuencia correcto, creyendo que es un paquete reenviado.

**RST Hijacking** :
==Implica inyectar un paquete de reinicio (RST) que parece auténtico mediante una dirección IP de origen falsificada y prediciendo el número de reconocimiento. El atacante puede restablecer la conexión de la víctima si utiliza un número de reconocimiento preciso.== La víctima cree que el origen ha enviado el paquete de reinicio y, por lo tanto, restablece la conexión. ==El secuestro RST se puede realizar utilizando herramientas de creación de paquetes, como **Colasoft Packet Builder, y herramientas de análisis de TCP/IP, como tcpdump.==**

**Blind Hijacking :** ==Un atacante puede inyectar datos maliciosos o comandos en las comunicaciones interceptadas de una sesión TCP, incluso si la víctima ha deshabilitado el enrutamiento de origen. Para ello, el atacante debe adivinar correctamente el siguiente ISN (Número de Secuencia Inicial) de una computadora que intenta establecer una conexión.==

**UDP Hijacking :** ==El Protocolo de Datagramas de Usuario (UDP) no utiliza secuenciación ni sincronización de paquetes, por lo que una sesión UDP es más fácil de atacar que una sesión TCP. Debido a que UDP es sin conexión, es fácil modificar datos sin que la víctima lo note. En un secuestro de sesión a nivel de red, el atacante falsifica una respuesta del servidor a una solicitud UDP del cliente antes de que el servidor pueda responder. De esta forma, el atacante toma el control de la sesión==

**MITM Attack Using Forged ICMP and ARP Spoofing** :
==Un ataque MITM (Man-in-the-Middle)* utiliza un sniffer de paquetes para interceptar la comunicación entre un cliente y un servidor. El atacante cambia la puerta de enlace predeterminada de la máquina del cliente e intenta redirigir los paquetes. Los paquetes entre el cliente y el servidor se enrutan a través del host del atacante mediante las siguientes dos técnicas:==

**▪ Forged Internet Control Message Protocol (ICMP) :** Un atacante puede usar ICMP para enviar mensajes falsificados que engañan al cliente y al servidor. En esta técnica, los paquetes ICMP son falsificados para redirigir el tráfico entre el cliente y el servidor a través del host del atacante.

**▪ Address Resolution Protocol (ARP) Spoofing** **:**Esta técnica implica engañar al host mediante la transmisión de solicitudes ARP y modificar sus tablas ARP enviando respuestas ARP falsificadas. El atacante envía respuestas ARP falsificadas que actualizan las tablas ARP del host, redirigiendo el tráfico hacia el host del atacante en lugar de la dirección IP legítima.

**PetitPotam Hijacking** **:** En un ataque PetitPotam, ==un atacante obliga a un controlador de dominio (DC) a iniciar una autenticación hacia el servidor del atacante. Para ello, el atacante utiliza la llamada a la API MS-EFSRPC de Microsoft para secuestrar la sesión de autenticación. El servidor SMB del atacante manipula la sesión para hacer que el controlador de dominio crea que el atacante es un usuario legítimo y, de esta forma, obtener el hash NTLM del controlador de dominio. Este ataque requiere que el atacante tenga credenciales válidas de un usuario legítimo dentro de la red==. Luego, el atacante retransmite la autenticación NTLM del controlador de dominio al Active Directory Certificate Services (AD CS) y genera un certificado.

