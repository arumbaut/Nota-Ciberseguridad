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
    
    - **Clave**: abuso de **tokens o servicios de sincronización** (Drive/Dropbox) — trafico inyectado indistinguible.
        

### Bloque III: Canal lateral y envoltorios

1. **Side-Channel / Cross-guest VM**
    
    - **Clave**: VM maliciosa en mismo host → ataques de **caché** (temporización, remanencia, acústico…).
        
2. **Wrapping Attack**
    
    - **Clave**: duplicado del **cuerpo SOAP** en la capa TLS → firma válida, ejecución de código malicioso.
        Se produce durante la traducción del mensaje SOAP en la capa TLS. El atacante duplica el cuerpo del mensaje y lo envía al servidor como si fuera un usuario legítimo

### Bloque IV: Ataques avanzados y malware

1. **Cloud Hopper**
    
    - **Clave**: phishing a MSP → **movimiento lateral** y C&C sin archivos (PowerShell, PowerSploit).
        Se desencadenan contra proveedores de servicios gestionados ([^5]MSP) y sus clientes. Una vez implementado con éxito, los atacantes pueden obtener acceso remoto a la propiedad intelectual e información crítica del MSP objetivo
        
2. **Cryptojacking**
    
    - **Clave**: scripts JS (CoinHive…) inyectados para **minería sigilosa** en navegadores.
        Consiste en el uso no autorizado del ordenador de la víctima para extraer criptomonedas de forma sigilosa. Los ataques de criptojacking son muy lucrativos e involucran tanto a atacantes externos como a infiltrados internos
        
3. **Cloudborne**
    
    - **Clave**: backdoor en **firmware** del servidor físico → persiste al reasignar IaaS.
        Vulnerabilidad que reside en un servidor en la nube físico que permite a los atacantes implantar una puerta trasera maliciosa en su firmware
        
4. ****Instance Metadata Service IMDS Attack**
    
    - **Clave**: explotar fallo de **Instance Metadata Service** → robar credenciales de roles.
        Explotan una vulnerabilidad de día cero en el servidor de aplicaciones objetivo o utilizando información filtrada a través de un proxy inverso implementado por los administradores
        
5. **Cloud Snooper**
    
    - **Clave**: GS mal configurado en AWS → rootkits que evaden firewall (puertos 80/443).
        Ataques de espionaje en la nube .Este ataque aprovechando un firewall mal configurado o cualquier vulnerabilidad subyacente
        
6. **Golden SAML**
    
    - **Clave**: manipular **assertions** SAML tras comprometer ADFS → creación de tokens falsos.
        Obtienen acceso administrativo al perfil de usuario del proveedor de identidad y explotan certificados de firma de tokens para generar tokens o respuestas SAML falsificados mediante la manipulación de las aserciones SAML
        
7. **Living Off the Cloud (LotC)**
    
    - **Clave**: uso de SaaS/IaaS legítimos para **exfiltrar datos** o lanzar DDoS / minería.
    - Atacantes atacan las aplicaciones SaaS e IaaS de las víctimas para llevar a cabo actividades maliciosas como la exfiltración de datos.