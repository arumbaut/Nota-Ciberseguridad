### **NTRODUCCIÓN A WINDOWS DEFENDER**

Microsoft Defender Antivirus (anteriormente Windows Defender) es la solución antivirus integrada en Windows 10 y 11.

**Historia rápida:**
- **Windows XP/Vista:** Microsoft Security Essentials (descarga separada)    
- **Windows 8/10/11:** Integrado y habilitado por defecto    
- **Evolución constante:** Ahora incluye protección en tiempo real, cloud, comportamental, ransomware, etc.   

**¿Es suficientemente bueno?**
- **Tests independientes (AV-Test, AV-Comparatives):** Puntuaciones comparables a antivirus de pago    
- **Ventajas:** Gratuito, integrado, no ralentiza el sistema, actualizaciones automáticas    
- **En entornos corporativos:** Se complementa con Microsoft Defender for Endpoint (EDR)

### **COMPONENTES DE PROTECCIÓN**

**1. Real-time Protection (Protección en tiempo real)** Escanea archivos en el momento en que se acceden, descargan o ejecutan.**Verificar estado:**
- `Get-MpComputerStatus | Select-Object RealTimeProtectionEnabled, AntivirusEnabled`    

**2. Cloud-delivered Protection (Protección en la nube)** Envía muestras de archivos sospechosos a Microsoft para análisis en la nube.
- Detección más rápida de nuevas amenazas    
- Base de datos actualizada constantemente    
- Respuesta en segundos ante amenazas emergentes    
- **Verificar estado:** `Get-MpComputerStatus | Select-Object *Cloud*`

**3. Automatic Sample Submission (Envío automático de muestras)** Envía muestras de archivos sospechosos a Microsoft automáticamente. **Habilitar envío automático de muestras:**
- `Set-MpPreference -SubmitSamplesConsent SendAllSamples`    

**4. Controlled Folder Access (Protección anti-ransomware)** Protege carpetas importantes contra modificaciones no autorizadas. Evita ransomware. **Carpetas protegidas por defecto:**
- Documentos    
- Imágenes    
- Videos    
- Música    
- Escritorio
    
**Habilitar Controlled Folder Access:**
- `Set-MpPreference -EnableControlledFolderAccess Enabled`

**5. Attack Surface Reduction (ASR) Rules** Reglas diseñadas para bloquear comportamientos comunes que utiliza el malware para infectar dispositivos. **Verificar reglas activas:**
- `Get-MpPreference | Select-Object -ExpandProperty AttackSurfaceReductionRules_Ids`    

**6. Network Protection** Protege el equipo contra sitios web maliciosos y ataques de phishing a nivel de red. **Habilitar Network Protection:**
- `Set-MpPreference -EnableNetworkProtection Enabled`

### **TIPOS DE ESCANEOS**

**1. Quick Scan (Escaneo rápido)** Escanea solo las áreas críticas donde suele esconderse el malware:
- **Memoria**    
- **Procesos en ejecución**    
- **Registro de inicio**    
- **Carpetas del sistema**

**Detalles:**
- **Duración:** 5-15 minutos típicamente.    
- **Comando PowerShell:** `Start-MpScan -ScanType QuickScan`    
**2. Full Scan (Escaneo completo)** Escanea TODO el sistema de archivos.
- **Detalle:** Puede tardar horas.    
- **Comando PowerShell:** `Start-MpScan -ScanType FullScan`

**3. Custom Scan (Escaneo personalizado)** Permite escanear rutas específicas de archivos o carpetas.

- **Ejemplo de comando:** `Start-MpScan -ScanType CustomScan -ScanPath "C:\Downloads"`    

**4. Offline Scan (Windows Defender Offline)** Diseñado para eliminar malware muy persistente (como rootkits) que se oculta mientras el sistema operativo está funcionando.
- **Funcionamiento:** Reinicia el equipo en un entorno de recuperación seguro.    
- **Ventaja:** Escanea sin que Windows esté cargado, impidiendo que el malware se defienda o se oculte.    
- **Comando PowerShell:** `Start-MpWDOScan`    
- **Ruta en Interfaz (GUI):** Seguridad de Windows → Protección contra virus → Opciones de examen → Examen sin conexión.  

**Verificación del estado:**
- Para consultar los resultados del último escaneo: `Get-MpComputerStatus | Select-Object *Scan*`

### **CIFRADO CON BITLOCKER**

BitLocker Drive Encryption es la solución de cifrado de disco completo (Full Disk Encryption - FDE) integrada en Windows.

**Protección ante:**
- Robo físico del equipo o disco duro.    
- Acceso no autorizado arrancando desde USB/LiveCD.    
- Venta o donación del equipo sin borrado seguro.    

**Qué cifra BitLocker:**
- Todo el volumen (incluyendo sistema operativo, archivos del sistema y datos de usuario).    
- Cifrado transparente: una vez desbloqueado, el sistema funciona normalmente.    
- Utiliza algoritmos de cifrado **AES-128** o **AES-256**.    

**Verificar disponibilidad:**
- Para comprobar si la característica está habilitada en el sistema: `Get-WindowsOptionalFeature -Online -FeatureName BitLocker`

### **¿Qué es TPM?**

El **TPM (Trusted Platform Module)** es un chip criptográfico de seguridad integrado en la placa base del equipo.

- **Genera y almacena claves** criptográficas de forma segura.    
- **Verifica la integridad del boot** (arranque) para asegurar que el sistema no haya sido manipulado.    
- **Seguridad física**: Las claves NUNCA salen del chip, lo que lo hace resistente a ataques de extracción.   

**Versiones:**
- **TPM 1.2**: Estándar antiguo.    
- **TPM 2.0**: Estándar actual y **requerido para Windows 11**.    
- **fTPM (Firmware TPM)**: Implementación basada en firmware común en procesadores AMD e Intel modernos.