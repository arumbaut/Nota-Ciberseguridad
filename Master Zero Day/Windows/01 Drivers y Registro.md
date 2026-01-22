**¿Qué son los drivers?**

- Software que permite al sistema operativo comunicarse con dispositivos de hardware.    
- Actúan como "traductores" entre el kernel y el hardware.    
- Sin driver apropiado, el hardware es inútil para el SO.    
- Ubicación de drivers: Kernel-mode: **C:\Windows\System32\drivers**.    

**Tipos de Drivers:**
- **Kernel-mode drivers (.sys)**    
    - Ejecutan en Ring 0 (modo kernel).        
    - Acceso directo y sin restricciones al hardware.        
    - Pueden acceder a toda la memoria del sistema.        
    - Riesgo: Un driver mal programado puede causar Blue Screen.        
    - Ejemplo: Driver de tarjeta gráfica NVIDIA (nvlddmkm.sys), driver de red Intel (e1d68x64.sys).
    - 
- **User-mode drivers**    
    - Ejecutan en Ring 3 (modo usuario).        
    - Acceso limitado, más seguros.        
    - Si fallan, no causan Blue Screen.        
    - Menos comunes, usados para dispositivos menos críticos.        
    - Ejemplo: Drivers de impresoras modernas, algunos drivers de cámaras web.
### **El Registro de Windows**
- **Definición:** Es una base de datos jerárquica centralizada.    
- **Propósito:** Almacena la configuración de bajo nivel del SO y de las aplicaciones.    
- **Historia:** Introducido en Windows 3.1 (1992) para reemplazar los archivos `.INI` dispersos.   
- **Analogía:** Se describe como el "sistema nervioso" de Windows, ya que casi cualquier aspecto del funcionamiento del sistema se configura aquí.
    
**Estructura Jerárquica:**
- Es similar a un sistema de archivos:   
    - **Keys (Claves):** Funcionan como carpetas.        
    - **Values (Valores):** Funcionan como los archivos o datos dentro de esas carpetas.        
- Las Keys pueden contener **Subkeys** (subcarpetas) y **Values** (los datos específicos de configuración).


**Los 5 Hives (Colmenas) principales:**

- **HKEY_LOCAL_MACHINE (HKLM)**    
    - Configuración de la MÁQUINA que aplica a todos los usuarios        
    - Hardware, servicios, drivers, software instalado para todos        
    - Requiere privilegios de administrador para modificar        
    - Ejemplo de uso: Configuración de servicios, drivers instalados
        
- **HKEY_CURRENT_USER (HKCU)**    
    - Configuración del usuario ACTUALMENTE logueado        
    - Preferencias personales, configuración de aplicaciones del usuario        
    - El usuario puede modificar sin ser admin        
    - Ejemplo: Configuración del escritorio, preferencias de Office
        
- **HKEY_USERS (HKU)**    
    - Contiene perfiles de TODOS los usuarios del sistema        
    - Formato: HKU\S-1-5-21-... (SID del usuario)

- **HKEY_CLASSES_ROOT (HKCR)**    
    - Asociaciones de extensiones de archivo con programas        
    - Información de objetos COM        
    - Ejemplo: .txt abre con notepad.exe, .pdf abre con Adobe Reader
        
- **HKEY_CURRENT_CONFIG (HKCC)**    
    - Información del perfil de hardware actual        
    - Menos usado en sistemas modernos (legacy de cuando se usaban hardware profiles)
        
- **Diferencia HKLM vs HKCU:**    
    - **HKLM**: Aplica a TODOS los usuarios del sistema        
    - **HKCU**: Solo al usuario actual

*_Ubicación física en disco: C:\Windows\System32\config*_

**Archivos sin extensión:**
- **SAM** → HKLM\SAM (Security Account Manager - cuentas locales)    
- **SECURITY** → HKLM\SECURITY (políticas de seguridad)    
- **SOFTWARE** → HKLM\SOFTWARE (software instalado)    
- **SYSTEM** → HKLM\SYSTEM (configuración del sistema)    
- **DEFAULT** → Perfil de usuario por defecto
    
**Herramientas para gestionar el Registro:**
- **regedit.exe** (Registry Editor)    
    - Editor gráfico estándar        
- Permite navegar, buscar, modificar, exportar, importar    
- **PRECAUCIÓN:** No hay "undo" - cambios son inmediatos