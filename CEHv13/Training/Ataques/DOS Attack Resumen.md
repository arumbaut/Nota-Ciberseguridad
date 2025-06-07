
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
    
    - **UDP flood**: puertos aleatorios → ICMP “Destino inalcanzable”.
        
    - **ICMP flood**: eco solicitudes masivas; respuesta satura ancho de banda.
        
    - **Ping of Death**: paquete >65 535 bytes → crash al reensamblar.
        
    - **Smurf**: IP source spoofed → broadcast ICMP → todos responden a la víctima.
        
    - **Pulse Wave**: pulsos gigantes (~300 Gbps) periódicos, muy difíciles de mitigar.
        
    - **Zero-day DDoS**: explota vulnerabilidades sin parche.
        
    - **NTP amplification**: “monlist” en NTP genera respuestas masivas.
        

### Bloque II: Protocolo

- **Objetivo**: agotar tablas de estado (pps/cps).
    
- **Handshake incompleto**:
    
    - **SYN flood**: nunca llega ACK.
        
    - **SYN-ACK flood**: explota fase 2.
        
    - **ACK/PUSH-ACK flood**: envía solo ACK o PUSH-ACK.
        
- **Fragmentation**: paquetes >1500 bytes fragmentados, consumen CPU al reensamblar.
    
- **Spoofed session floods**: crear sesiones TCP falsas (Multiple SYN-ACK, Multiple ACK).
    
- **TCP SACK Panic**: paquetes SACK malformados → integer overflow → kernel panic.
    

### Bloque III: Capa de aplicación

- **Objetivo**: agotar conexiones rps.
    
- **HTTP flood** (GET/POST):
    
    - **Single-Session**: múltiples solicitudes en una sola sesión.
        
    - **Single-Request**: varias dentro de un solo paquete.
        
    - **Recursive GET**: recorre lista de URLs.
        
    - **Random Recursive GET**: finge navegación en foros/blogs con páginas aleatorias.
        
- **Slowloris**: solicitudes HTTP parciales mantenidas abiertas.
    
- **UDP app-layer flood**: protocolos UDP de capa 7 (ej. DNS sobre UDP).
    

### Bloque IV: Varios y avanzados

- **Multi-Vector**: cambia o combina vectores (e.g. SYN + HTTP flood).
    
- **P2P Attack**: usa redes P2P vulnerables, sin bots centralizados.
    
- **Permanent DoS (PDoS)**: sabotea hardware (phlashing).
    
- **DRDoS**: reflexión distribuida—zombis envían a reflectores; tráfico masivo hacia la víctima.
    
- **Ransom DDoS**: extorsión; muestra ataque y exige rescate.
    

---

## 3. Técnica de Loci + Mnemotecnia

Imagina un **centro de mando en 4 salas**:

1. **Sala Volumétrica**:
    
    - Un río de agua (flood) y un cañón de amplificación con un cartel NTP, DNS, SSDP.
        
    - Una bomba de pulso (Pulse Wave) haciendo latidos, un reloj marcando “Zero-day”, y un poste “65 538 bytes” (Ping of Death) al lado de una gran carpa “Smurf” llena de espejos para broadcast.
        
2. **Sala Protocolo**:
    
    - Tres guardias incompletos dando mano (SYN sin completar).
        
    - Una cinta transportadora de fragmentos gigantes.
        
    - Un teatro de marionetas TCP enviando ACK/PUSH-ACK.
        
    - Un kernel gigante asustado por un “SACK” malformado.
        
3. **Sala App-Layer**:
    
    - Un navegador atascado con pestañas HTTP GET y POST (parciales).
        
    - Una hilera de foros con páginas numeradas (Recursive).
        
    - Slowloris como un anciano que nunca termina de hablar.
        
    - Un surtidor UDP de capa 7.
        
4. **Sala Avanzada**:
    
    - Un maestro de ceremonias cambiando disfraces (Multi-Vector).
        
    - Una red P2P hecha de manos entrelazadas.
        
    - Un martillo golpeando un servidor (PDoS).
        
    - Varios espejos reflectores apuntando a un blanco (DRDoS).
        
    - Un chantajista con un sobre de dinero frente a un servidor (Ransom).