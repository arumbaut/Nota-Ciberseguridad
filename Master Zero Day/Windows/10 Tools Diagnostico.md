### **TABLA DE ENRUTAMIENTO**

**¿Qué es la tabla de enrutamiento?**
La tabla de enrutamiento de Windows define cómo se envían los paquetes a diferentes destinos. Ver tabla de enrutamiento:
- **cmd > route print**    
- **powershell > Get-NetRoute -AddressFamily IPv4 | Format-Table**    

**Traceroute (Trazar ruta)**
Para ver por dónde pasan tus paquetes hacia un destino:
- **cmd > tracert google.com**    
- **powershell > Test-NetConnection -TraceRoute google.com**


**ping - Conectividad básica**
Ping envía paquetes ICMP Echo Request y espera Echo Reply.
**cmd**
- **ping google.com** # 4 paquetes    
- **ping google.com -t** # Continuo (Ctrl+C para parar)    
- **ping google.com -n 10** # 10 paquetes    
- **ping 192.168.1.1** # Ping al gateway
    
**powershell**
- **Test-Connection google.com**    
- **Test-Connection google.com -Count 10**    
- **Test-NetConnection google.com -Port 443**    

**Interpretación:**
- **"Respuesta desde..."**: Conectividad OK    
- **"Tiempo de espera agotado"**: Paquetes perdidos (puede ser firewall bloqueando ICMP)    
- **"Host de destino inaccesible"**: No hay ruta al destino    
- **Tiempo (ms)**: Latencia (< 20ms excelente LAN, < 100ms bueno Internet)

**netstat - Conexiones activas**
Ver conexiones de red activas:
**cmd**
- **netstat**: Conexiones TCP activas    
- **netstat -a**: Todas las conexiones y puertos en escucha    
- **netstat -ano**: Con PID del proceso    
- **netstat -ano | findstr 443**: Filtrar por puerto específico
    
**powershell**
- **Get-NetTCPConnection**    
- **Get-NetTCPConnection -State Established**    
- **Get-NetTCPConnection -LocalPort 443**