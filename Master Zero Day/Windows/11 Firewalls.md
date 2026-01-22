**INTRODUCCIÓN AL FIREWALL**

El firewall es tu primera línea de defensa contra ataques de red. Actúa como un filtro que decide qué tráfico puede entrar y salir de tu equipo.

Windows tiene un firewall integrado desde Windows XP SP2 (2004), pero ha mejorado mucho desde entonces. En Windows 10/11 se llama Windows Defender Firewall (anteriormente Windows Firewall).

**Funciones principales:**
- **Filtrar tráfico entrante** (conexiones que llegan a tu equipo)    
- **Filtrar tráfico saliente** (conexiones que salen de tu equipo)    
- **Aplicar reglas diferentes según el tipo de red** (perfiles)    
- **Integración con IPsec** para cifrado de red    

**Importante:** El firewall está habilitado por defecto y NO deberías deshabilitarlo nunca. Si algo no funciona, la solución es crear una regla específica, no apagar el firewall.

**Ver si el firewall está activo:**
- **powershell > Get-NetFirewallProfile | Select-Object Name, Enabled**

**Perfiles de red?**
**¿Qué son los perfiles de red?**

Windows Defender Firewall tiene tres perfiles, cada uno con su propio conjunto de reglas. El perfil depende del tipo de red a la que estés conectado.

**1. Domain (Dominio):**
- Se activa cuando el equipo está conectado a una red donde puede contactar con su Domain Controller    
- Es el perfil más permisivo (porque se asume que la red corporativa es confiable)    
- Las reglas se pueden gestionar centralmente vía Group Policy    
- Ejemplo: tu portátil de empresa en la oficina    

**2. Private (Privado):**
- Para redes privadas de confianza (casa, oficina pequeña)    
- Más restrictivo que Domain, pero permite detección de red y compartir archivos    
- Ejemplo: tu red Wi-Fi de casa    
- Permite que otros equipos te vean en la red
### **3. Public (Público):**
- **Uso:** Para redes no confiables (cafeterías, aeropuertos, hoteles).    
- **Seguridad:** Es el más restrictivo; bloquea la detección de red y el compartir archivos.    
- **Ejemplo:** Wi-Fi de Starbucks.    
- **Efecto:** Tu equipo es "invisible" para otros en la red.    

**PowerShell**
- `Get-NetConnectionProfile`    
- `Get-NetConnectionProfile | Format-List *`

### **Reglas de firewall**
El firewall funciona con reglas. Cada regla especifica:
1. **Dirección:** Entrante (Inbound) o Saliente (Outbound)    
2. **Acción:** Permitir (Allow) o Bloquear (Block)    
3. **Programa/Servicio:** Qué aplicación afecta (opcional)    
4. **Puerto y Protocolo:** TCP/UDP y número de puerto (opcional)   
5. **Alcance:** Direcciones IP origen/destino (opcional)    
6. **Perfiles:** Domain, Private, Public (uno o más)

### **ARQUITECTURA DEL FIREWALL**

**Tipos de reglas**
**1. Reglas de programa:**
- Aplican a una aplicación específica (ej. Chrome.exe)    
- Permiten TODO el tráfico de ese programa    
- Ejemplo: "Permitir Chrome.exe entrante y saliente"   

**2. Reglas de puerto:**
- Aplican a un puerto TCP o UDP específico    
- Independientes del programa    
- Ejemplo: "Permitir TCP puerto 80 entrante"    

**3. Reglas predefinidas:**
- Windows incluye muchas reglas predefinidas para servicios comunes    
- Ejemplos: "Compartir archivos e impresoras", "Escritorio remoto", "Detección de red"

Aquí tienes la extracción de texto íntegra de la nueva imagen proporcionada (**image_1db5f9.png**) sobre las reglas entrantes y salientes, junto con un resumen consolidado de toda la información compartida hasta ahora.

### **REGLAS ENTRANTES Y SALIENTES**

**Reglas Entrantes (Inbound Rules)** Controlan conexiones que LLEGAN a tu equipo desde la red.
- **Comportamiento predeterminado:** Bloquear todo EXCEPTO lo explícitamente permitido whitelist approach).    
- Esto es lo más seguro.    
- **PowerShell:** `Get-NetFirewallRule -Direction Inbound -Enabled True`.   

**Reglas Salientes (Outbound Rules)** Controlan conexiones que SALEN de tu equipo hacia la red.
- **Comportamiento predeterminado:** Permitir todo por defecto.    
- Esto es menos seguro, pero más conveniente para usuarios.    
- **PowerShell:** `Get-NetFirewallRule -Direction Outbound -Enabled True`.    

**En entornos de alta seguridad:** Se cambia a "bloquear todo saliente" y se permiten solo conexiones específicas (más trabajo, pero mucho más seguro).

### **LOGS DEL FIREWALL**

**Habilitar logging** Por defecto, el firewall NO registra las conexiones bloqueadas o permitidas (para no llenar el disco).
**GUI:**
- **wf.msc** → Clic derecho en "Windows Defender Firewall con seguridad avanzada" → Propiedades    
- En cada perfil (Domain, Private, Public) → Personalizar    
- Registrar paquetes descartados: **Sí**    
- Registrar conexiones correctas: **Sí** (opcional, genera MUCHO log)    
- Ubicación del archivo de registro por defecto: `%SystemRoot%\System32\LogFiles\Firewall\pfirewall.log`
    

**PowerShell:**

- `Set-NetFirewallProfile -Profile Domain,Private,Public -LogBlocked True` # Habilitar logging para paquetes bloqueados    
- `Set-NetFirewallProfile -Profile Domain,Private,Public -LogMaxSizeKilobytes 4096` # Tamaño máximo del log (en KB)    

**Ver logs** El archivo de log es texto plano:
- `Get-Content C:\Windows\System32\LogFiles\Firewall\pfirewall.log -Tail 50`
    

---