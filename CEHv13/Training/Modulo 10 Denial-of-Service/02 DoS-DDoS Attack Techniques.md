#### Basic Categories of DoS/DDoS Attack Vectors 

### ▪ Volumetric Attacks 
Estos ataques agotan el ancho de banda, ya sea dentro de la red/servicio objetivo o entre la red/servicio objetivo y el resto de Internet, causando bloqueos de tráfico y previniendo el acceso de los usuarios legítimos. La magnitud del ataque se mide en bits por segundo (bps). Los ataques volumétricos DDoS generalmente atacan protocolos como **Network Time Protocol (NTP), Domain Name System (DNS) y Simple Service Discovery Protocol (SSDP)**, los cuales son sin estado y no tienen características integradas de evitación de congestión. La generación de una gran cantidad de paquetes puede causar el consumo de todo el ancho de banda en la red.

#### Hay dos tipos de ataques de agotamiento de ancho de banda

**Ø En un ataque de inundación (flood attack)**, los zombis envían grandes volúmenes de tráfico a los sistemas de la víctima para agotar el ancho de banda de estos sistemas.

**Ø En un ataque de amplificación (amplification attack)**, el atacante o los zombis transfieren mensajes a una dirección IP de difusión. Este método amplifica el tráfico malicioso que consume el ancho de banda de los sistemas de la víctima.

**Volumetric attack techniques**  

**Ø User Datagram Protocol (UDP) flood attack:** 
Un atacante envía paquetes UDP falsificados a una tasa de paquetes muy alta a un host remoto en puertos aleatorios de un servidor objetivo utilizando un gran rango de direcciones IP de origen. La inundación de paquetes UDP hace que el servidor verifique repetidamente la existencia de aplicaciones que no existen en esos puertos. Como resultado, las aplicaciones legítimas se vuelven inaccesibles por el sistema, y cualquier intento de acceder a ellas devuelve una respuesta de error con un paquete ICMP de "Destino inalcanzable".

**Ø Internet Control Message Protocol (ICMP) flood attack:**
En este ataque, los atacantes envían grandes volúmenes de paquetes ICMP de solicitud de eco a un sistema víctima directamente o a través de redes de reflexión. Estos paquetes indican al sistema víctima que responda, y el gran volumen de tráfico satura el ancho de banda de la conexión de red de la víctima, lo que hace que se sobrecargue y posteriormente deje de responder a las solicitudes legítimas TCP/IP.Para protegerse contra los ataques de inundación ICMP, es necesario establecer un umbral que active la función de protección contra ataques de inundación ICMP cuando se exceda.

**:TiJewishStar: Ø Ping of Death (PoD) attack:**
En un ataque Ping of Death (PoD), un atacante intenta bloquear, desestabilizar o congelar el sistema o servicio objetivo enviando paquetes malformados o sobredimensionados utilizando un comando de ping simple. Supongamos que un atacante envía un paquete de **65,538 bytes** al servidor web objetivo. Este tamaño excede el límite de tamaño prescrito por **RFC 791 IP**, **que es 65,535 bytes**. El proceso de reensamblaje realizado por el sistema receptor podría causar que el sistema se bloquee.

**:TiJewishStar: Ø Smurf attack :**
En un ataque Smurf, el atacante falsifica la dirección IP de origen con la dirección IP de la víctima y envía una gran cantidad de paquetes ICMP ECHO request a una red de difusión IP. Esto provoca que todos los hosts en la red de difusión respondan a las solicitudes ICMP ECHO recibidas. Estas respuestas se envían a la máquina de la víctima debido a que la dirección IP fue falsificada por el atacante, lo que provoca un tráfico significativo hacia la máquina de la víctima y, finalmente, hace que se bloquee.

**Ø  Pulse Wave DDoS Attack**

Son el tipo más reciente de ataques DDoS .el patrón de ataque es periódico, y el ataque es enorme, consumiendo todo el ancho de banda de las redes objetivo. Los atacantes envían una cadena altamente repetitiva de paquetes como pulsos al objetivo cada 10 minutos, y la sesión de ataque dura aproximadamente una hora o algunos días. Un solo pulso (300 Gbps o más) es más que suficiente para saturar un conducto de red. La recuperación de tales ataques es muy difícil y, en ocasiones, imposible.

**Ø Zero-day attack**
Los ataques DDoS de día cero son ataques en los que las vulnerabilidades DDoS no tienen parches ni mecanismos defensivos efectivos. Hasta que la víctima identifique la estrategia de ataque del actor de amenazas y despliegue un parche para la vulnerabilidad DDoS explotada, el atacante bloquea activamente todos los recursos de la víctima y roba los datos de la víctima.stos ataques pueden causar un daño severo a la infraestructura de red y los activos de la víctima.


**Ø NTP amplification attack**
En un ataque de amplificación NTP, el atacante utiliza una botnet para enviar grandes paquetes UDP a través de una dirección IP falsificada (IP real de la víctima) hacia el servidor NTP. Generalmente se inicia a través de un servidor NTP que tiene habilitado el comando monlist. Cada paquete UDP provoca una solicitud al servidor NTP mediante el comando monlist, lo que resulta en la producción de grandes paquetes de respuesta. El servidor comienza a responder inmediatamente a la dirección IP falsificada. Como resultado, la dirección IP de la víctima se ve inundada con grandes respuestas, causando que la infraestructura de red circundante se vea inundada con tráfico no deseado.


### ▪ Protocol Attacks
Los ataques DDoS de protocolo **agotan los recursos disponibles** en el objetivo o en un dispositivo específico entre el objetivo y la Internet. Estos ataques **consumen las tablas de estado de conexión presentes en dispositivos de infraestructura de red** como balanceadores de carga, cortafuegos y servidores de aplicaciones. Como resultado, no se permitirán nuevas conexiones, ya que el dispositivo estará esperando a que las conexiones existentes se cierren o expiren.

En este caso, la magnitud del ataque se mide en paquetes por segundo (pps) o conexiones por segundo (cps).

#### Protocol attack techniques:  

**Ø Synchronize (SYN) flood attack:**
En un ataque SYN, el atacante **envía una gran cantidad de solicitudes SYN al servidor objetivo (víctima)** **con direcciones IP de origen falsas.** El ataque crea conexiones TCP incompletas que agotan los recursos de la red. El atacante envía una solicitud SYN falsa al servidor objetivo. Después de que el servidor envía un SYN/ACK en respuesta a la solicitud del cliente (atacante), el cliente nunca envía una respuesta ACK. Esto deja al servidor esperando para completar la conexión.

**SYN-ACK Flood Attack:** Este tipo de ataque es similar al ataque SYN flood, excepto que en este tipo de ataque de inundación, el atacante explota la segunda etapa de un apretón de manos de tres vías enviando una gran cantidad de paquetes SYN-ACK

**ACK and PUSH ACK Flood Attack:** En un ataque ACK y PUSH ACK flood, los atacantes envían una gran cantidad de paquetes ACK y PUSH ACK falsificados a la máquina objetivo, lo que hace que esta deje de funcionar.

**Ø Fragmentation attack**
Estos ataques destruyen la capacidad de una víctima para reensamblar los paquetes fragmentados al inundarla con fragmentos TCP o UDP. En los ataques de fragmentación, el atacante envía una gran cantidad de paquetes fragmentados (de más de 1500 bytes) a un servidor web objetivo con una tasa de paquetes relativamente baja. Dado que el protocolo permite la fragmentación, estos paquetes generalmente no son inspeccionados mientras pasan por equipos de red como enrutadores, cortafuegos y el sistema de detección de intrusos (IDS) o el sistema de prevención de intrusos (IPS).El reensamblaje e inspección de estos paquetes grandes y fragmentados consume recursos excesivos. Además, el contenido de los fragmentos de los paquetes es aleatorizado por el atacante, lo que hace que el reensamblaje y la inspección consuman más recursos y, a su vez, provoque que el sistema se caiga.

**Ø Spoofed session flood attack**
En este tipo de ataque, los atacantes crean sesiones TCP falsas o falsificadas enviando múltiples paquetes SYN, ACK, RST o FIN. Los atacantes emplean este ataque para eludir cortafuegos y realizar ataques DDoS contra redes objetivo, agotando sus recursos de red.
Ejemplos de  Spoofed session flood attack

**▪ Multiple SYN-ACK Spoofed Session Flood Attack**
Los atacantes crean una sesión falsa con múltiples paquetes SYN y múltiples paquetes ACK, junto con uno o más paquetes RST o FIN.

**▪ Multiple ACK Spoofed Session Flood Attack**
Los atacantes crean una sesión falsa omitiendo completamente los paquetes SYN y utilizando únicamente múltiples paquetes ACK junto con uno o más paquetes RST o FIN. Debido a que no se emplean paquetes SYN y los cortafuegos generalmente usan filtros de paquetes SYN para detectar tráfico anómalo, la tasa de detección de DDoS de los cortafuegos es muy baja para estos ataques.

Ø Acknowledgement (ACK) flood attack
Ø SYN-ACK flood attack
Ø ACK and PUSH ACK flood attack 
Ø TCP connection flood attack 
Ø TCP state exhaustion attack 
Ø RST attack 


**Ø TCP SACK Panic Attack**
Es un vector de ataque remoto en el que los atacantes intentan hacer que una máquina Linux se bloquee enviando paquetes SACK con un tamaño de segmento máximo (MSS) malformado. Este ataque explota una vulnerabilidad de desbordamiento de entero en el Linux Socket Buffer (SKB), lo que puede llevar a un pánico del kernel.

### ▪ Application Layer Attacks

El atacante intenta explotar vulnerabilidades en el protocolo de la capa de aplicación o en la propia aplicación para impedir que los usuarios legítimos accedan a la aplicación. Los recursos de la capa de aplicación o de la aplicación se consumen abriendo conexiones y dejándolas abiertas hasta que no se puedan realizar nuevas conexiones. Estos ataques destruyen un aspecto específico de una aplicación o servicio y pueden ser efectivos con una o pocas máquinas atacantes que generen una baja tasa de tráfico. Además, estos ataques son muy difíciles de detectar y mitigar. La magnitud del ataque se mide en solicitudes por segundo (rps).

**Application layer attack techniques:** 

****Ø Hypertext Transfer Protocol (HTTP) flood attack**

**Un ataque HTTP GET/POST** es un ataque sofisticado de capa 7 que no utiliza paquetes mal formados, suplantación (spoofing) ni técnicas de reflexión. Este tipo de ataque requiere menos ancho de banda que otros ataques para derribar el sitio o servidor web objetivo

**En un ataque HTTP GET** el atacante utiliza un encabezado HTTP con retraso en el tiempo para mantener una conexión HTTP abierta y agotar los recursos del servidor web. El atacante nunca envía la solicitud completa al servidor de destino. Como resultado, el servidor mantiene la conexión HTTP abierta y espera, lo que hace que el servidor sea inaccesible para los usuarios legítimos. En estos tipos de ataques, todos los parámetros de red parecen estar saludables, mientras que el servicio sigue siendo inaccesible.

**En un ataque HTTP POST**, el atacante envía solicitudes HTTP con encabezados completos, pero con un cuerpo de mensaje incompleto al servidor web o la aplicación de destino. Debido a que el cuerpo del mensaje está incompleto, el servidor espera el resto del cuerpo, haciendo que el servidor web o la aplicación web no estén disponibles para los usuarios legítimos

**▪ Single-Session HTTP Flood Attack :** Un atacante explota las vulnerabilidades en HTTP 1.1 para bombardear un objetivo con múltiples solicitudes dentro de una sola sesión HTTP.

**▪ Single-Request HTTP Flood Attack****:** Este tipo de ataque implica que el atacante realice múltiples solicitudes HTTP dentro de una sola sesión HTTP, ocultando estas solicitudes dentro de un solo paquete HTTP.

**▪ Recursive HTTP GET Flood Attack** **:** El ataque GET recursivo recopila una lista de páginas o imágenes y parece estar navegando a través de estas páginas o imágenes. Sin embargo, realiza ataques de inundación sigilosos sobre el objetivo

**▪ Random Recursive GET Flood Attack:** Este tipo de ataque es una versión modificada del ataque GET recursivo. Está diseñado para foros, blogs y otros sitios web que tienen páginas en secuencia. Finge estar navegando a través de páginas. Debido a que los objetivos son foros, grupos y otros blogs, el atacante utiliza números aleatorios de un rango de páginas válido para hacerse pasar por un usuario legítimo y envía una nueva solicitud GET cada vez.

**Ø Slowloris attack**
Slowloris es una herramienta de ataque DDoS utilizada para realizar ataques de capa 7 (Capa de Aplicación) y derribar infraestructuras web. Se distingue de otras herramientas porque utiliza tráfico HTTP legítimo para tumbar un servidor objetivo. En los ataques Slowloris, el atacante envía solicitudes HTTP parciales al servidor web o aplicación objetivo. Al recibir estas solicitudes parciales, el servidor objetivo abre múltiples conexiones y espera a que las solicitudes se completen. Sin embargo, estas solicitudes permanecen incompletas, lo que provoca que la piscina de conexiones concurrentes máximas del servidor se llene, y los intentos de conexión adicionales son denegados.

**Ø UDP application layer flood attack**
Son conocidos por su naturaleza volumétrica, algunos protocolos de capa de aplicación que dependen de UDP pueden ser utilizados por los atacantes para realizar ataques de inundación en redes objetivo

**Ø Multi-Vector Attack**

En los ataques DDoS multi-vector, el atacante utiliza combinaciones de ataques volumétricos. En este tipo de ataque, el atacante cambia rápidamente de un tipo de ataque DDoS (por ejemplo, paquetes SYN) a otro (como un ataque de capa 7).Los ataques pueden ser lanzados de manera secuencial (uno tras otro) o en paralelo a través de múltiples vectores.

**Ø Peer-to-Peer Attack**

Ataque distribuido de denegación de servicio en el que el atacante explota vulnerabilidades o fallos en las redes o servidores peer-to-peer (P2P) para inundar el sistema objetivo con tráfico.Este ataque se distingue de los ataques tradicionales basados en botnets en que no depende de máquinas o bots comprometidos. Pueden ser muy disruptivos para sitios web o servicios en línea.

**Ø Permanent Denial-of-Service Attack**

El Ataque de Denegación de Servicio Permanente (PDoS), también conocido como phlashing, tiene como objetivo principal el hardware y causa daños irreversibles al mismo. A diferencia de otros tipos de ataques de denegación de servicio (DoS), el ataque PDoS no se dirige a sobrecargar los recursos del sistema, sino que sabotea el hardware, lo que obliga a la víctima a reemplazar o reinstalar el hardware afectado.

**Ø Distributed Reflection Denial-of-Service (DRDoS) Attack**

Un ataque DRDoS explota la vulnerabilidad en el protocolo de la tres vías de conexión TCP. Este ataque involucra una máquina atacante, víctimas intermediarias (zombis), víctimas secundarias (reflectores) y una máquina objetivo. El atacante lanza este ataque enviando solicitudes a las máquinas intermediarias, que a su vez reflejan el tráfico del ataque hacia el objetivo.Un ataque DRDoS es un ataque inteligente porque es muy difícil, o incluso imposible, rastrear al atacante. En lugar del atacante real, las víctimas secundarias (reflectores) parecen atacar directamente al objetivo. Este ataque es más eficaz que un típico ataque DDoS porque múltiples víctimas intermediarias y secundarias generan un ancho de banda de ataque masivo.

**Ø DDoS Extortion/Ransom DDoS (RDDoS) Attack**

El ataque de extorsión DDoS también se conoce como DDoS por rescate (RDDoS). En este tipo de ataque, los atacantes amenazan a las organizaciones objetivo con realizar un ataque DDoS e insisten en que paguen una cantidad específica como rescate. El atacante puede enviar una nota de rescate o iniciar un ataque DDoS de muestra utilizando una botnet sobre recursos específicos de la organización para hacerles creer que la amenaza es real.