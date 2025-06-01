==**La inspección de paquetes** (_Packet sniffing_) es el proceso de **monitorear y capturar todos los paquetes de datos** que pasan por una red determinada, utilizando una aplicación de software o un dispositivo de hardware. La inspección es sencilla en redes basadas en _hubs_, ya que el tráfico en un segmento pasa por todos los equipos conectados a ese segmento. Sin embargo, la mayoría de las redes actuales funcionan con _switches__==._ La principal diferencia entre un hub y un switch es que un hub transmite los datos de línea a todos los puertos de la máquina sin ningún tipo de mapeo, mientras que un switch analiza la dirección MAC (Media Access Control) asociada a cada trama que lo atraviesa y envía los datos únicamente al puerto correspondiente. Un programa de inspección de paquetes (también conocido como sniffer) solo puede capturar paquetes de datos dentro de una subred determinada, lo que significa que no puede espiar paquetes de otra red.

There are two basic types of Ethernet environments, and sniffers work differently in each. These two types are:

**▪ Ethernet Compartido (Shared Ethernet)**

En un entorno de Ethernet compartido, un único bus conecta a todos los hosts que compiten por el ancho de banda.  
En este escenario, todas las demás máquinas reciben los paquetes destinados a una sola máquina. El sniffing en un entorno de Ethernet compartido es pasivo, y por lo tanto difícil de detectar. Sin embargo, una máquina que ejecuta un sniffer ignora esta regla y acepta todos los paquetes.

### ▪ Ethernet Conmutado (Switched Ethernet)

En un entorno de Ethernet conmutado, los hosts se conectan a través de un switch en lugar de un hub.  
El switch mantiene una tabla que rastrea la dirección MAC de cada computadora y el puerto físico al que está conectada, para así entregar los paquetes directamente a la máquina de destino.Un switch solo envía paquetes a la computadora de destino específica; no los transmite a todas las computadoras en la red.Esto permite un mejor aprovechamiento del ancho de banda disponible y mejora la seguridad.Por esta razón, poner la NIC de una máquina en modo promiscuo para capturar paquetes no funciona como en una red conmutada. 

#### Aunque un switch es más seguro que un hub, es posible realizar sniffing en la red utilizando los siguientes métodos:

**▪ Suplantación ARP (ARP [^1]Spoofing)****:**

ARP es sin estado. ==Una máquina puede enviar una respuesta ARP incluso sin haberla solicitado; además, puede aceptar tal respuesta. Cuando una máquina quiere esnifar el tráfico originado desde otro sistema, puede hacer un ARP spoofing al gateway de la red. La caché ARP de la máquina objetivo tendrá una entrada incorrecta para el gateway. Por lo tanto, todo el tráfico destinado a pasar por el gateway pasará ahora por la máquina que falsificó la dirección MAC del gateway.==

**▪ MAC Flooding**
Los switches mantienen una tabla de traducción que mapea diversas direcciones MAC a los puertos físicos en el switch. Como resultado, pueden enrutar paquetes de manera inteligente de un host a otro. ==Sin embargo, los switches tienen memoria limitada. El MAC flooding aprovecha esta limitación para bombardear a los switches con direcciones MAC falsas hasta que los switches ya no pueden seguir el ritmo. Una vez que esto le sucede a un switch, entra en modo de falla abierta, en el que empieza a actuar como un hub, transmitiendo paquetes a todos los puertos del switch==. Una vez que esto ocurre, se vuelve fácil realizar sniffing. macof es una utilidad que viene con el conjunto dsniff y ayuda al atacante a realizar MAC flooding.




[^1]: Suplantación
