## 1. Chunking: Agrupa los ataques en 4 bloques temáticos

|**Bloque**|**Ataques incluidos**|
|---|---|
|**I. Robo de credenciales**|Service Hijacking (Social Engineering), Session Hijacking (XSS y Session Riding)|
|**II. Interceptación de comunicaciones**|Service Hijacking (Network Sniffing), Man-in-the-Cloud|
|**III. Canal lateral y envoltorios**|Side-Channel / Cross-guest VM, Wrapping Attack|
|**IV. Ataques avanzados y malware**|Cloud Hopper, Cryptojacking, Cloudborne, IMDS, Cloud Snooper, Golden SAML, LotC|

---

## 2. Para cada bloque: resumen y puntos clave

### Bloque I: Robo de credenciales

1. **Service Hijacking (Social Engineering)**
    
    - **Clave**: robo de credenciales por **phishing**, pharming, ingeniería social.
        
    - **Objetivo**: restablecer contraseñas en CSP o TI.
        
2. **Session Hijacking via XSS**
    
    - **Clave**: inyección de **JavaScript** roba **cookies** de sesión.
        
3. **Session Riding**
    
    - **Clave**: CSRF — engaño al usuario a clicar un enlace malicioso **durante** sesión activa.
        

### Bloque II: Interceptación de comunicaciones

1. **Service Hijacking (Network Sniffing)**
    
    - **Clave**: uso de **Wireshark**, captura de credenciales _sin cifrar_.
        
2. **Man-in-the-Cloud (MITC)**
    
    - **Clave**: abuso de **tokens de sincronización** (Drive/Dropbox) — trafico inyectado indistinguible.
        

### Bloque III: Canal lateral y envoltorios

1. **Side-Channel / Cross-guest VM**
    
    - **Clave**: VM maliciosa en mismo host → ataques de **caché** (temporización, remanencia, acústico…).
        
2. **Wrapping Attack**
    
    - **Clave**: duplicado del **cuerpo SOAP** en la capa TLS → firma válida, ejecución de código malicioso.
        

### Bloque IV: Ataques avanzados y malware

1. **Cloud Hopper**
    
    - **Clave**: phishing a MSP → **movimiento lateral** y C&C sin archivos (PowerShell, PowerSploit).
        
2. **Cryptojacking**
    
    - **Clave**: scripts JS (CoinHive…) inyectados para **minería sigilosa** en navegadores.
        
3. **Cloudborne**
    
    - **Clave**: backdoor en **firmware** del servidor físico → persiste al reasignar IaaS.
        
4. **IMDS Attack**
    
    - **Clave**: explotar fallo de **Instance Metadata Service** → robar credenciales de roles.
        
5. **Cloud Snooper**
    
    - **Clave**: GS mal configurado en AWS → rootkits que evaden firewall (puertos 80/443).
        
6. **Golden SAML**
    
    - **Clave**: manipular **assertions** SAML tras comprometer ADFS → creación de tokens falsos.
        
7. **Living Off the Cloud (LotC)**
    
    - **Clave**: uso de SaaS/IaaS legítimos para **exfiltrar datos** o lanzar DDoS / minería.