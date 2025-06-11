
|**Bloque**|**Categorías y técnicas**|
|---|---|
|**I. Volumétricos**|Flood, Amplificación, UDP flood, ICMP flood, Ping of Death, Smurf, Pulse Wave, Zero-day, NTP amplification|
|**II. Protocolo**|SYN flood, SYN-ACK flood, ACK/PUSH-ACK flood, Fragmentation, Spoofed session floods (Multiple SYN-ACK, Multiple ACK), TCP SACK Panic|
|**III. Capa de aplicación**|HTTP GET/POST flood (Single-Session, Single-Request, Recursive, Random Recursive), Slowloris, UDP app-layer flood|
|**IV. Varios y avanzados**|Multi-Vector, P2P, Permanent (PDoS), DRDoS, Ransom DDoS|

---

## 2. Resumen y **puntos clave** por bloque

### Bloque I: Volumétricos

- **Objetivo**: agotar ancho de banda (bps).
    
- **Flood vs Amplificación**:
    
    - _Flood_: zombis envían tráfico directo.
        
    - _Amplificación_: uso de servidores NTP/DNS/SSDP para aumentar el volumen.
        
- **Técnicas destacadas**:
    
    - **UDP flood**: envía paquetes UDP falsificados a una tasa de paquetes muy alta a un host remoto en puertos aleatorios de un servidor objetivo utilizando un gran rango de direcciones IP de origen.
        
    - **ICMP flood**: envían grandes volúmenes de paquetes ICMP de solicitud de eco a un sistema víctima directamente o a través de redes de reflexión. Estos paquetes indican al sistema víctima que responda, y el gran volumen de tráfico satura el ancho de banda de la conexión de red de la víctima
        
    - **Ping of Death**: intenta bloquear, desestabilizar o congelar el sistema o servicio objetivo enviando paquetes malformados o sobredimensionados utilizando un comando de ping simple.
        
    - **Smurf**: el atacante falsifica la dirección IP de origen con la dirección IP de la víctima y envía una gran cantidad de paquetes ICMP ECHO request a una red de difusión IP. Esto provoca que todos los hosts en la red de difusión respondan a la victima las solicitudes ICMP ECHO recibidas.
        
    - **Pulse Wave**: el patrón de ataque es periódico, y el ataque es enorme, consumiendo todo el ancho de banda de las redes objetivo. Los atacantes envían una cadena altamente repetitiva de paquetes como pulsos al objetivo cada 10 minutos.
        
    - **Zero-day DDoS**: son ataques en los que las vulnerabilidades DDoS no tienen parches ni mecanismos defensivos efectivos. Hasta que la víctima identifique la estrategia de ataque del actor de amenazas y despliegue un parche para la vulnerabilidad DDoS explotada, el atacante bloquea activamente todos los recursos de la víctima y roba los datos de la víctima
        
    - **NTP amplification**: el atacante utiliza una botnet para enviar grandes paquetes UDP a través de una dirección IP falsificada (IP real de la víctima) hacia el servidor NTP. Generalmente se inicia a través de un servidor NTP que tiene habilitado el comando monlist..
        

### Bloque II: Protocolo

- **Objetivo**: agotar tablas de estado (pps/cps).
    
- **Handshake incompleto**:
    
    - **SYN flood**: el atacante **envía una gran cantidad de solicitudes SYN al servidor objetivo (víctima)** **con direcciones IP de origen falsas.** El ataque crea conexiones TCP incompletas que agotan los recursos de la red.
        
    - **SYN-ACK flood**: similar al ataque SYN flood, excepto que en este tipo de ataque de inundación, el atacante explota la segunda etapa de un apretón de manos de tres vías enviando una gran cantidad de paquetes SYN-ACK.
        
    - **ACK/PUSH-ACK flood**: los atacantes envían una gran cantidad de paquetes ACK y PUSH ACK falsificados a la máquina objetivo, lo que hace que esta deje de funcionar..
        
- **Fragmentation**: destruyen la capacidad de una víctima para reensamblar los paquetes fragmentados al inundarla con fragmentos TCP o UDP. En los ataques de fragmentación, el atacante envía una gran cantidad de paquetes fragmentados (de más de 1500 bytes) a un servidor web objetivo con una tasa de paquetes relativamente baja. .
    
- **Spoofed session floods**:  los atacantes crean sesiones TCP falsas o falsificadas enviando múltiples paquetes SYN, ACK, RST o FIN. Los atacantes emplean este ataque para eludir cortafuegos y realizar ataques DDoS contra redes objetivo, agotando sus recursos de red..

- **Multiple SYN-ACK Spoofed Session Flood Attack**
	Los atacantes crean una sesión falsa con múltiples paquetes SYN y múltiples paquetes ACK, junto con uno o más paquetes RST o FIN.
	
	Multiple ACK Spoofed Session Flood Attack**
	Los atacantes crean una sesión falsa omitiendo completamente los paquetes SYN y utilizando únicamente múltiples paquetes ACK junto con uno o más paquetes RST o FIN. Debido a que no se emplean paquetes SYN y los cortafuegos generalmente usan filtros de paquetes SYN para detectar tráfico anómalo, la tasa de detección de DDoS de los cortafuegos es muy baja para estos ataques.
    
- **TCP SACK Panic**: Es un vector de ataque remoto en el que los atacantes intentan hacer que una máquina Linux se bloquee enviando paquetes SACK con un tamaño de segmento máximo (MSS) malformado. Este ataque explota una vulnerabilidad de desbordamiento de entero en el Linux Socket Buffer
    

### Bloque III: Capa de aplicación

- **Objetivo**: agotar conexiones rps.
    
- **HTTP flood** (GET/POST):
    
    - **Single-Session**: Un atacante explota las vulnerabilidades en HTTP 1.1 para bombardear un objetivo con múltiples solicitudes dentro de una sola sesión HTTP.
        
    - **Single-Request**:  el atacante realice múltiples solicitudes HTTP dentro de una sola sesión HTTP, ocultando estas solicitudes dentro de un solo paquete HTTP.
        
    - **Recursive GET**: recopila una lista de páginas o imágenes y parece estar navegando a través de estas páginas o imágenes. Sin embargo, realiza ataques de inundación sigilosos sobre el objetivo.
        
    - **Random Recursive GET**: versión modificada del ataque GET recursivo. Está diseñado para foros, blogs y otros sitios web que tienen páginas en secuencia. Finge estar navegando a través de páginas. Debido a que los objetivos son foros, grupos y otros blogs, el atacante utiliza números aleatorios de un rango de páginas válido para hacerse pasar por un usuario legítimo y envía una nueva solicitud GET cada vez..
        
- **Slowloris**:  En los ataques Slowloris, el atacante envía solicitudes HTTP parciales al servidor web o aplicación objetivo. Al recibir estas solicitudes parciales, el servidor objetivo abre múltiples conexiones y espera a que las solicitudes se completen.  .
    
- **UDP app-layer flood**: conocidos por su naturaleza volumétrica, algunos protocolos de capa de aplicación que dependen de UDP pueden ser utilizados por los atacantes para realizar ataques de inundación en redes objetivo
    

### Bloque IV: Varios y avanzados

- **Multi-Vector**: el atacante utiliza combinaciones de ataques volumétricos. En este tipo de ataque, el atacante cambia rápidamente de un tipo de ataque DDoS (por ejemplo, paquetes SYN) a otro (como un ataque de capa 7)..
    
- **P2P Attack**: Ataque distribuido de denegación de servicio en el que el atacante explota vulnerabilidades o fallos en las redes o servidores peer-to-peer (P2P) para inundar el sistema objetivo con tráfico.
    
- **Permanent DoS (PDoS)**:también conocido como phlashing, tiene como objetivo principal el hardware y causa daños irreversibles al mismo. A diferencia de otros tipos de ataques de denegación de servicio (DoS), el ataque PDoS no se dirige a sobrecargar los recursos del sistema, sino que sabotea el hardware
    
- **DRDoS**: explota la vulnerabilidad en el protocolo de la tres vías de conexión TCP. Este ataque involucra una máquina atacante, víctimas intermediarias (zombis), víctimas secundarias (reflectores) y una máquina objetivo
    
- **Ransom DDoS**: se conoce como DDoS por rescate (RDDoS). En este tipo de ataque, los atacantes amenazan a las organizaciones objetivo con realizar un ataque DDoS e insisten en que paguen una cantidad específica como rescate
    
 