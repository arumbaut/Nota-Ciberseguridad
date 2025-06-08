**▪ Passive Session Hijacking :** En un ataque pasivo, después de secuestrar una sesión, un atacante solo observa y graba todo el tráfico durante la sesión. Ejemplo el sniffing de contraseñas

**▪ Active Session Hijacking :** En un ataque activo, un atacante toma el control de una sesión existente, ya sea rompiendo la conexión en un lado de la conversación o participando activamente. Un ejemplo de un ataque activo es un ataque de intermediario (MITM).


**▪ Network-Level Hijacking** **:** ==El **secuestro de sesión a nivel de red** es la interceptación de paquetes durante la transmisión entre un cliente y un servidor en una sesión **TCP/UDP**==

**▪ Application-Level Hijacking** **:** ==El secuestro de sesión a nivel de aplicación implica tomar el control de la sesión de usuario del Protocolo de Transferencia de Hipertexto (HTTP) mediante la obtención de los IDs de sesión==. A nivel de aplicación, el atacante toma el control de una sesión existente y puede crear nuevas sesiones no autorizadas utilizando datos robados.

|                                                          |                                                                                                    |                                                                                                                    |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Características**                                      | **Secuestro de sesión ciego (Blind Hijacking)**                                                    | **Suplantación (Spoofing)**                                                                                        |
| **Objetivo del ataque**                                  | Tomar control de una sesión activa preexistente.                                                   | Falsificar la identidad de un usuario o máquina para iniciar una nueva sesión.                                     |
| **Tipo de ataque**                                       | Activo, toma control de una sesión ya establecida.                                                 | Activo, inicia una nueva sesión utilizando credenciales robadas.                                                   |
| **Dependencia de la predicción de números de secuencia** | Necesita predecir los números de secuencia de la sesión en curso.                                  | Necesita predecir los números de secuencia para suplantar una sesión.                                              |
| **Intercepción de tráfico**                              | El atacante no puede observar las respuestas directamente (ciego).                                 | El atacante puede observar y registrar el tráfico, pero no tiene control directo sobre la sesión.                  |
| **Dependencia de ruteo de origen**                       | Puede usar el ruteo de origen para interceptar el tráfico.                                         | El ruteo de origen puede ser útil, pero no esencial para la suplantación.                                          |
| **Requiere conocimientos previos del ISN**               | Sí, debe conocer el número de secuencia inicial (ISN) y los paquetes involucrados.                 | Sí, debe conocer los números de secuencia para iniciar la conexión suplantada.                                     |
| **Método de ejecución**                                  | El atacante interrumpe y predice los números de secuencia para tomar control de una sesión activa. | El atacante inicia una sesión desde cero con credenciales robadas, sin necesidad de interrumpir una sesión activa. |
| **Interacción con el host víctima**                      | Se requiere desplazar al usuario legítimo de la sesión (DoS) antes de tomar el control.            | No es necesario desplazar al usuario legítimo; se inicia una nueva sesión.                                         |
| **Requiere control sobre la sesión del usuario**         | Sí, el atacante debe tener control sobre la sesión para "tomarla".                                 | No necesariamente, ya que el atacante puede crear una nueva sesión desde cero.                                     |
| **Resistencia a la autenticación**                       | Más difícil, requiere herramientas especializadas.                                                 | Depende de la capacidad de adivinar o suplantar las credenciales.                                                  |

Application-Level Session Hijacking

**Techniques**

**▪ Stealing:** El atacante tpuede usar herramientas de "sniffing" como Wireshark o Riverbed Packet Analyzer Plus para interceptar el tráfico entre el cliente y el servidor y extraer los IDs de sesión de los paquetes.

**▪ Guessing:** Un atacante intenta adivinar los IDs de sesión observando las variables de la sesión. En el caso del secuestro de sesión, el rango de valores de ID de sesión que se pueden adivinar es limitado. Por lo tanto, las técnicas de adivinación son efectivas solo cuando los servidores usan mecanismos débiles o defectuosos para la generación de IDs de sesión.

**▪ Brute forcing:** Un atacante obtiene los IDs de sesión intentando todas las permutaciones posibles de valores de IDs de sesión hasta encontrar uno que funcione

A session token can be compromised in various ways:
▪ Session sniffing
▪ Predictable session token
▪ Man-in-the-middle (MITM) attack
▪ Man-in-the-browser attack
▪ Cross-site scripting (XSS) attack
▪ Cross-site request forgery attack
▪ Session replay attack
▪ Session fixation attack
▪ CRIME attack
▪ Forbidden attack
▪ Session donation attack
▪ PetitPotam hijacking

**Compromising Session IDs Using Sniffing** **:** Un atacante utiliza herramientas de "packet sniffing" como Wireshark y Riverbed Packet Analyzer Plus **para interceptar el tráfico HTTP entre una víctima y el servidor web**. 

**Compromising Session IDs by Predicting Session Token** **:** Normalmente, los atacantes pueden predecir los IDs de sesión generados por algoritmos débiles e impersonar a un usuario del sitio web.

**Compromising Session IDs Using Man-in-the-Middle/Manipulator-in-the-Middle Attack**
Man-in-the-Middle (MITM) o Manipulator-in-the-Middle (MITM) se utiliza para infiltrarse en una conexión existente entre sistemas e interceptar los mensajes que se están transmitiendo. 

**Compromising Session IDs Using Man-in-the-Browser/Manipulator-in-the-Browser Attack**

Un ataque Man-in-the-Browser (MITB) o Manipulator-in-the-Browser (MITB) es similar a un ataque MITM, pero la diferencia entre ambos es que un ataque MITB utiliza un caballo de Troya para interceptar y manipular las llamadas entre un navegador y sus mecanismos o bibliotecas de seguridad. 

==**Compromising Session IDs Using Client-side Attacks**==
Los ataques del lado del cliente ocurren cuando los clientes establecen conexiones con servidores maliciosos y procesan datos potencialmente dañinos de estos servidores.

**Session Hijacking Using Session Donation Attack** **:** ==El atacante dona su propia sesión válida al usuario objetivo. El atacante primero obtiene una ID de sesión válida al iniciar sesión en un servicio y luego envía esa misma ID de sesión al usuario objetivo. Cuando el usuario hace clic en el enlace y ingresa sus detalles (nombre de usuario, contraseña, datos de pago, etc.), esos datos se vinculan a la cuenta del atacante sin que la víctima lo sepa.== 

**Compromising Session IDs Using ==Client-side Attacks: Cross-site Script Attack**==

 ==Ocurre cuando una página web dinámica recibe datos maliciosos del atacante y los ejecuta en el sistema del usuario. los atacantes pueden insertar un JavaScript, VBScript, ActiveX, HTML o un applet Flash malicioso en una página dinámica vulnerable. Esa página luego ejecuta el script en la máquina del usuario y puede recopilar información personal, robar cookies, redirigir a los usuarios a páginas web inesperadas o ejecutar cualquier código malicioso en el sistema del usuario.==

**Compromising Session IDs Using Client-side Attacks: ==Cross-site Request Forgery Attack(CSRF)**==

==La falsificación de solicitud entre sitios (CSRF), también conocida como ataque de un solo clic, es un ataque en el que el atacante explota la sesión activa de la víctima== . ==A diferencia de un ataque XSS, que explota la confianza que un usuario tiene en un sitio web en particular, el CSRF explota la confianza que un sitio web tiene en el navegador de un usuario.==

**Compromising Session IDs Using Session Replay Attacks** :
==El atacante captura el token de autenticación de un usuario escuchando una conversación entre el usuario y el servidor. Una vez que el token de autenticación es capturado,  reproduce la solicitud de autenticación al servidor con el token de autenticación capturado para evadir al servidor; como resultado, obtiene acceso no autorizado al servidor.==

**Compromising Session IDs Using ==Session Fixation== :** 
==Un ataque de fijación de sesión fija una sesión establecida en el navegador del usuario; por lo tanto, el ataque se inicia antes de que el usuario inicie sesión. El atacante usa diversas técnicas para realizar un ataque de fijación de sesión: Token de sesión en el argumento de la URL, Token de sesión en un campo de formulario oculto, ID de sesión en una cookie==
 

==**Session Hijacking Using Proxy Servers**== **:** ==Un atacante induce a la víctima a hacer clic en un enlace falso que parece legítimo, pero que redirige al usuario al servidor del atacante. Luego, el atacante reenvía la solicitud al servidor legítimo en nombre de la víctima y actúa como un intermediario para toda la transacción. Al actuar como un proxy, el atacante captura la información de la sesión durante la interacción entre el servidor legítimo y el usuario.==

**Session Hijacking Using CRIME Attack** :
==Es un ataque del lado del cliente que explota vulnerabilidades en la característica de compresión de datos de protocolos como SSL/Transport Layer Security (TLS), SPDY y HTTP Secure (HTTPS)==.  ==Los atacantes usan herramientas como CrimeCheck para detectar si un servidor web tiene habilitada la compresión TLS o HTTP, y por lo tanto, es vulnerable a ataques CRIME==. 

**Session Hijacking Using Forbidden Attack** **:** ==Este ataque explota la vulnerabilidad de que la implementación de TLS reutiliza incorrectamente el mismo "nonce" (un número único usado una vez)cuando los datos se cifran utilizando el modo de cifrado avanzado Galois/Counter (AES-GCM) durante el apretón de manos TLS. Explotan esta vulnerabilidad para realizar un ataque MITM generando claves criptográficas usadas para la autenticación.== Al repetir el mismo nonce durante el apretón de manos TLS, un atacante puede monitorear y secuestrar la conexión.

# **The following are different types of network-level hijacking:**
**▪ Blind hijacking**
**▪ UDP hijacking**
**▪ TCP/IP hijacking**
**▪ RST hijacking**
**▪ Man-in-the-middle: packet sniffer**
**▪ IP spoofing: source routed packets**

**Blind Hijacking :** ==Un atacante puede inyectar datos maliciosos o comandos en las comunicaciones interceptadas de una sesión TCP, incluso si la víctima ha deshabilitado el enrutamiento de origen. Para ello, el atacante debe adivinar correctamente el siguiente ISN (Número de Secuencia Inicial) de una computadora que intenta establecer una conexión.==

**TCP/IP Hijacking** **:** ==Un atacante intercepta una conexión establecida entre dos partes que se comunican, utilizando paquetes falsificados y luego finge ser una de esas partes.== En este enfoque, ==el atacante usa paquetes falsificados para redirigir el tráfico TCP a su propia máquina. 

**RST Hijacking** :
==Implica inyectar un paquete de reinicio (RST) que parece auténtico mediante una dirección IP de origen falsificada y prediciendo el número de reconocimiento. El atacante puede restablecer la conexión de la víctima si utiliza un número de reconocimiento preciso.==  ==El secuestro RST se puede realizar utilizando herramientas de creación de paquetes, como **Colasoft Packet Builder, y herramientas de análisis de TCP/IP, como tcpdump.==**

**UDP Hijacking :**  
==En un secuestro de sesión a nivel de red, el atacante falsifica una respuesta del servidor a una solicitud UDP del cliente antes de que el servidor pueda responder. De esta forma, el atacante toma el control de la sesión==

**MITM Attack Using Forged ICMP and ARP Spoofing** :
==Un ataque MITM (Man-in-the-Middle)* utiliza un sniffer de paquetes para interceptar la comunicación entre un cliente y un servidor. El atacante cambia la puerta de enlace predeterminada de la máquina del cliente e intenta redirigir los paquetes. Los paquetes entre el cliente y el servidor se enrutan a través del host del atacante mediante las siguientes dos técnicas:==

**▪ Forged Internet Control Message Protocol (ICMP) :** ==Un atacante puede usar ICMP para enviar mensajes falsificados que engañan al cliente y al servidor. En esta técnica, los paquetes ICMP son falsificados para redirigir el tráfico entre el cliente y el servidor a través del host del atacante.==

**▪ Address Resolution Protocol (ARP) Spoofing** **:**
==Esta técnica implica engañar al host mediante la transmisión de solicitudes ARP y modificar sus tablas ARP enviando respuestas ARP falsificadas. El atacante envía respuestas ARP falsificadas que actualizan las tablas ARP del host, redirigiendo el tráfico hacia el host del atacante en lugar de la dirección IP legítima.==

**PetitPotam Hijacking** **:** ==Un atacante obliga a un controlador de dominio (DC) a iniciar una autenticación hacia el servidor del atacante.  El servidor SMB del atacante manipula la sesión para hacer que el controlador de dominio crea que el atacante es un usuario legítimo y, de esta forma, obtener el hash NTLM del controlador de dominio. Este ataque requiere que el atacante tenga credenciales válidas de un usuario legítimo dentro de la red==. 


