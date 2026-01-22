**CONCEPTOS BÁSICOS DE NETWORKING EN WINDOWS**

**Modelo TCP/IP**

Windows usa el stack TCP/IP como protocolo de red. Esto significa que sigue el modelo de capas:

1. **Capa de Aplicación:** HTTP, DNS, SMB, RDP, etc.    
2. **Capa de Transporte:** TCP (conexiones fiables) o UDP (sin conexión)    
3. **Capa de Red:** IP (direccionamiento lógico)    
4. **Capa de Enlace:** Ethernet, Wi-Fi (direccionamiento físico - MAC)

**CONCEPTOS BÁSICOS DE NETWORKING EN WINDOWS**

**Elementos básicos de configuración de red**
Para que un equipo funcione en red necesita:
1. **Dirección IP:** Identificador único en la red (ej. 192.168.1.100)    
2. **Máscara de subred:** Define qué parte de la IP es red y qué parte es host (ej. 255.255.255.0)  
3. **Gateway predeterminado:** Router que conecta con otras redes/Internet (ej. 192.168.1.1)    
4. **Servidor DNS:** Traduce nombres a IPs (ej. 8.8.8.8, 1.1.1.1)

**CONCEPTOS BÁSICOS DE NETWORKING EN WINDOWS**

**IP Estática vs. DHCP**
- **IP Estática (Manual):**    
    - Configuras manualmente todos los parámetros        
    - La IP no cambia nunca (a menos que la cambies tú)        
    - Usado en servidores, impresoras de red, equipos críticos
        
- **DHCP (Dinámica):**    
    - El equipo obtiene automáticamente la configuración de un servidor DHCP        
    - La IP puede cambiar cuando expira el "lease" (alquiler)        
    - Usado en equipos cliente (portátiles, PCs de escritorio)

**COMANDOS BÁSICOS DE RED**

**CMD**
- **ipconfig**    
- **ipconfig /all** # Más detallado
    
**POWERSHELL**
- **Get-NetIPConfiguration** # Ver todas las interfaces y su configuración    
- **Get-NetIPConfiguration -Detailed** # Ver con más detalle    
- **Get-NetIPAddress -AddressFamily IPv4 | Where-Object {$_.InterfaceAlias -notlike "_Loopback_"}** # Ver solo interfaces activas con IPv4    
- **Get-NetIPConfiguration -InterfaceAlias "Ethernet"** # Ver configuración de una interfaz específica

Aquí tienes la extracción de texto de la imagen proporcionada (**image_1b8226.jpg**) sobre los adaptadores de red:

**CONCEPTOS BÁSICOS DE NETWORKING EN WINDOWS**

**Adaptadores de red**
Windows puede tener múltiples adaptadores de red:
**Adaptadores físicos:**
- **Ethernet (NIC - Network Interface Card):** Cable RJ45    
- **Wi-Fi (WLAN):** Inalámbrico    
- **Bluetooth:** Para redes PAN (Personal Area Network)   

**Adaptadores virtuales:**
- **Hyper-V Virtual Ethernet Adapter:** Para máquinas virtuales    
- **VMware Network Adapter:** Si usas VMware    
- **VirtualBox Host-Only Adapter:** Si usas VirtualBox    
- **VPN adapters:** Cuando te conectas a una VPN (ej. TAP-Windows, WireGuard)    
- **Loopback (127.0.0.1):** Interfaz virtual para comunicación local

**Comandos para Adaptadores de red**
- **Get-NetAdapter** # Ver todos los adaptadores    
- **Get-NetAdapter | Where-Object {$_.Status -eq "Up"}** # Ver solo los habilitados    
- **Get-NetAdapter | Format-List *** # Ver con más detalle    
- **Get-NetAdapterStatistics** # Ver información física (velocidad, duplex, etc.)

**Dirección MAC (Physical Address)**

Cada adaptador de red tiene una dirección MAC única de 48 bits (6 bytes en hexadecimal).
- **Formato:** 00-1A-2B-3C-4D-5E o 00:1A:2B:3C:4D:5E    
- **Primeros 3 bytes (24 bits): OUI** (Organizationally Unique Identifier) - Identifican al fabricante    
- **Últimos 3 bytes (24 bits):** Identificador único del dispositivo    

**Ver direcciones MAC:**
**cmd**
- **ipconfig /all** # Ver en la línea "Dirección física"    
- **getmac** # Ver todas las MACs    

**powershell > Get-NetAdapter | Select-Object Name, MacAddress, Status**