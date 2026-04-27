

### 1. Broadcast (Difusión)

El mensaje se envía desde un emisor a **absolutamente todos** los dispositivos de la misma red local (VLAN).

- **Cómo funciona:** El switch recibe el paquete y lo clona por todos sus puertos. No importa si el receptor quiere la información o no; su tarjeta de red tendrá que procesarla para ver si le sirve.
    
- **Dirección MAC:** Siempre es $FF:FF:FF:FF:FF:FF$.
    
- **Uso común:** Protocolo ARP (cuando tu PC pregunta "¿quién tiene esta IP?") o cuando un dispositivo busca un servidor DHCP para obtener una IP.
    
- **Problema:** Si hay mucho broadcast, la red se satura (tormentas de broadcast).
    
### 2. Multicast (Multidifusión)

Es como un "grupo de WhatsApp". El mensaje se envía desde un emisor a un **grupo específico** de dispositivos que han decidido "suscribirse" a ese flujo de datos.

- **Cómo funciona:** Los dispositivos interesados se unen a un grupo (usando el protocolo IGMP). El switch guarda los dispositivos en una tabla IGMP. El switch/router inteligente solo envía el tráfico a los puertos donde sabe que hay alguien escuchando.
    
- **Dirección IP:** Utiliza el rango de Clase D ($224.0.0.0$ a $239.255.255.255$).
    
- **Uso común:** Streaming de video (IPTV), videoconferencias múltiples, actualizaciones de protocolos de enrutamiento (como OSPF o RIPv2) o despliegue de imágenes de Windows a varios PCs a la vez.
    
- **Ventaja:** Es mucho más eficiente que el broadcast porque no molesta a los dispositivos que no están interesados.
- Es necesario que el switch sea gestionable y ademas permita IGMP

###### En IPv6 el  *Neighbor Discovery Protocol (NDP)* la manera en que va a descubrir la *MAC Address* para una dirección IP no es mediante *Broadcast* como en IPv4 con el protocolo *ARP* sino mediante *Multicast*

El **Neighbor Discovery Protocol (NDP)** es para **IPv6** lo que el ARP es para IPv4, pero mucho más inteligente y completo. Mientras que en IPv4 dependemos de gritos (Broadcast) para encontrar a otros, NDP utiliza el **Multicast**, lo que lo hace mucho más eficiente.

Funciona sobre el protocolo **ICMPv6** y se encarga de que los dispositivos en una red local puedan "conocerse" y comunicarse.

### Resolución de Direcciones (Sustituto de ARP)

Cuando un equipo conoce la IP de un vecino pero no su dirección MAC, utiliza dos mensajes:

- **Neighbor Solicitation (NS):** El equipo envía un mensaje preguntando: _"¿Quién tiene esta IP?"_. A diferencia de IPv4, este mensaje no va a todos ($FF:FF:FF$), sino a un grupo de **Multicast** específico (Solicited-Node Multicast).
    
- **Neighbor Advertisement (NA):** El dueño de la IP responde con su dirección MAC.

![[Pasted image 20260421124655.png|640]]