**¿Qué es DNS?**

DNS (Domain Name System) es el sistema que traduce nombres legibles para humanos (como google.com) a direcciones IP (como 142.250.185.46).

Sin DNS, tendrías que memorizar direcciones IP para todo. DNS es como la agenda telefónica de Internet.

**Proceso de resolución DNS**
1. **Cache local del navegador**    
    - ↓ (no encontrado)        
2. **Cache DNS del sistema operativo (Windows DNS Client)**    
    - ↓ (no encontrado)        
3. **Consulta al servidor DNS configurado (ej. 8.8.8.8)**    
    - ↓        
4. **Si el servidor DNS no lo sabe, pregunta a otros servidores DNS (recursión)**    
    - ↓        
5. **Respuesta: [www.ejemplo.com](https://www.ejemplo.com) = 93.184.216.34**    
    - ↓        
6. **Windows guarda la respuesta en caché (TTL = Time To Live)**

**Servidores DNS públicos populares:**
- **Google:** 8.8.8.8 y 8.8.4.4    
- **Cloudflare:** 1.1.1.1 y 1.0.0.1    

**Comandos**
- **nslookup** - Consulta DNS interactiva:    
    - `nslookup google.com`        
    - `nslookup google.com 8.8.8.8` # Usar servidor DNS específico        
- **Resolve-DnsName** - PowerShell moderno:    
    - `Resolve-DnsName google.com`        
    - `Resolve-DnsName google.com -Server 8.8.8.8`        
    - `Resolve-DnsName google.com -Type MX` # Registros de mail        
    - `Resolve-DnsName google.com -Type A` # Solo IPv4

- **Get-DnsClientCache** # Ver la caché    
- **Clear-DnsClientCache** # Limpiar la caché DNS (útil para troubleshooting)


**DNS EN ACTIVE DIRECTORY**

**En entornos corporativos con Active Directory:**
- **Los Domain Controllers actúan como servidores DNS**    
- **El DNS no solo resuelve nombres de Internet, también nombres internos del dominio**   
- **Es crítico que los equipos del dominio apunten a los DNS del dominio, no a DNS públicos**  
- **Los DNS del dominio pueden reenviar consultas externas a DNS públicos**    

**Configuración típica en dominio:**
- **DNS Primario:** Dirección IP del Domain Controller (ej. 10.0.0.10)    
- **DNS Secundario:** Otro DC o un DNS público como backup (ej. 8.8.8.8)    

**Sufijo DNS** El sufijo DNS se añade automáticamente a nombres sin dominio completo.

Por ejemplo, si tu sufijo es empresa.local y escribes ping servidor:
- **Windows prueba primero:** servidor.empresa.local    
- **Si falla, prueba con solo servidor**

