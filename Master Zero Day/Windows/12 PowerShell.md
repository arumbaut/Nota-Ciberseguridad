### **INTRODUCCIÓN A POWERSHELL**

**¿Qué es PowerShell?**

PowerShell es mucho más que una simple línea de comandos. Es un shell de línea de comandos y un lenguaje de scripting basado en .NET Framework que está diseñado específicamente para la administración de sistemas.

**Diferencias con CMD (Command Prompt):**

| **Aspecto**      | **CMD**             | **PowerShell**             |
| ---------------- | ------------------- | -------------------------- |
| Edad             | Desde MS-DOS (1981) | Desde 2006                 |
| Tipo de comandos | Comandos de texto   | Cmdlets (objetos .NET)     |
| Output           | Texto plano         | Objetos estructurados      |
| Pipeline         | Pasa texto          | Pasa objetos               |
| Extensibilidad   | Limitada            | Módulos, funciones, clases |
| Scripting        | Batch (.bat)        | Scripts (.ps1)             |

### **¿Por qué PowerShell?**

- **Automatización:** Tareas repetitivas se hacen en segundos.    
- **Consistencia:** Sintaxis uniforme en todos los comandos.    
- **Potencia:** Acceso completo al sistema y .NET Framework.    
- **Objetos:** No procesas texto, procesas objetos con propiedades y métodos.    
- **Remoting:** Administra equipos remotos fácilmente.

### **¿Qué es un Cmdlet?**

Un cmdlet (se pronuncia "command-let") es el comando básico de PowerShell. NO es un ejecutable, es código .NET compilado.

**Convención de nomenclatura: Verbo-Sustantivo**
- **Get-Process**: # Obtener procesos    
- **Stop-Service**: # Detener servicio    
- **New-Item**: # Crear elemento    
- **Remove-User**: # Eliminar usuario    
- **Set-Location**: # Establecer ubicación

### **Verbos aprobados**

PowerShell tiene una lista de verbos aprobados para mantener consistencia:

| **Verbo**   | **Significado**      | **Ejemplos**                                  |
| ----------- | -------------------- | --------------------------------------------- |
| **Get**     | Obtener información  | `Get-Process`, `Get-Service`, `Get-ChildItem` |
| **Set**     | Establecer/modificar | `Set-Location`, `Set-ExecutionPolicy`         |
| **New**     | Crear algo nuevo     | `New-Item`, `New-Service`                     |
| **Remove**  | Eliminar             | `Remove-Item`, `Remove-Service`               |
| **Start**   | Iniciar              | `Start-Process`, `Start-Service`              |
| **Stop**    | Detener              | `Stop-Process`, `Stop-Service`                |
| **Enable**  | Habilitar            | `Enable-PSRemoting`                           |
| **Disable** | Deshabilitar         | `Disable-NetAdapter`                          |
| **Test**    | Probar/verificar     | `Test-Connection`, `Test-Path`                |
| **Invoke**  | Invocar/ejecutar     | `Invoke-Command`, `Invoke-WebRequest`         |

### **Sintaxis**

La estructura general para ejecutar un comando es:
**Cmdlet -Parameter1 Value1 -Parameter2 Value2**
**Ejemplo:** **Get-Process -Name chrome -ComputerName servidor01**

### **Cmdlets esenciales**

**# Navegación**
- **Get-Location**: # pwd en Linux, cd en CMD    
- **Set-Location C:\Users**: # cd    
- **Get-ChildItem**: # dir en CMD, ls en Linux    

**# Ayuda**
- **Get-Help Get-Process**    
- **Get-Help Get-Process -Examples**    
- **Get-Help Get-Process -Full**    
- **Get-Help Get-Process -Online**: # Abre navegador con ayuda online    

**# Información del sistema**
- **Get-Process**: # Procesos en ejecución    
- **Get-Service**: # Servicios    
- **Get-EventLog**: # Logs de eventos    
- **Get-ComputerInfo**: # Información del equipo

### **ALIAS**

**# Alias estilo CMD**
- **dir** → `Get-ChildItem`    
- **cd** → `Set-Location`    
- **cls** → `Clear-Host`    
- **copy** → `Copy-Item`    
- **del** → `Remove-Item`    
- **move** → `Move-Item`    
- **type** → `Get-Content`
    
**# Alias estilo Linux**
- **ls** → `Get-ChildItem`    
- **pwd** → `Get-Location`    
- **cat** → `Get-Content`    
- **man** → `Get-Help`    
- **ps** → `Get-Process`    
- **kill** → `Stop-Process`

### **¿Qué es el Pipeline?**

El pipeline (|) conecta cmdlets pasando objetos de uno a otro. Esto es lo que hace a PowerShell tan poderoso.
**# Obtener procesos que usan más de 100MB de memoria** `Get-Process | Where-Object {$_.WorkingSet -gt 100MB} | Sort-Object WorkingSet -Descending`

**# Desglose:**
- **# 1. Get-Process**: Obtiene todos los procesos (objetos Process)    
- **# 2. Where-Object**: Filtra objetos que cumplen condición    
- **# 3. Sort-Object**: Ordena por propiedad WorkingSet

### **¿Qué es un módulo?**

Un módulo es una colección de cmdlets, funciones y otros recursos agrupados. Los módulos extienden la funcionalidad de PowerShell.

**# Listar módulos cargados** `Get-Module`
**# Listar TODOS los módulos disponibles** `Get-Module -ListAvailable`

**# Módulos importantes:**
- **NetAdapter:** → Gestión de adaptadores de red    
- **NetTCPIP:** → Configuración TCP/IP    
- **NetSecurity:** → Firewall    
- **DnsClient:** → Cliente DNS    
- **ActiveDirectory:** → Gestión de AD (si está instalado)    
- **Hyper-V:** → Gestión de VMs    
- **Storage:** → Discos y volúmenes

### **Importar módulos**

La mayoría se cargan automáticamente cuando usas un cmdlet del módulo, pero puedes importar manualmente:

**# Importar módulo**`Import-Module NetSecurity`
**# Ver cmdlets de un módulo**`Get-Command -Module NetSecurity`
**# Eliminar módulo de la sesión**`Remove-Module NetSecurity`

### **POLÍTICAS DE EJECUCIÓN**

¿Qué son las Execution Policies?
Las políticas de ejecución son una característica de seguridad que controla qué scripts pueden ejecutarse. NO es un control de seguridad robusto (puede bypassearse fácilmente), sino una protección contra ejecución accidental de scripts.

# Ver política actual
Get-ExecutionPolicy
# Ver políticas en todos los ámbitos
Get-ExecutionPolicy -List

|**Política**|**Descripción**|
|---|---|
|**Restricted**|No se permite ejecutar ningún script (solo cmdlets interactivos)|
|**AllSigned**|Solo scripts firmados por un editor confiable|
|**RemoteSigned**|Scripts locales sin firma OK, scripts remotos deben estar firmados|
|**Unrestricted**|Todos los scripts, pero aviso para scripts remotos|
|**Bypass**|No hay restricciones ni avisos (peligroso)|
|**Undefined**|No hay política establecida|


### **ÁMBITOS DE POLÍTICAS**

Las políticas se aplican en diferentes ámbitos (del más específico al más general):
- **Process**: Sólo para el proceso actual de PowerShell    
- **CurrentUser**: Para el usuario actual    
- **LocalMachine**: Para todos los usuarios del equipo    

Gana la política más restrictiva.
**Ámbitos de políticas**
Las políticas NO son seguridad real. Pueden bypassearse:
- `powershell -ExecutionPolicy Bypass -File script.ps1`