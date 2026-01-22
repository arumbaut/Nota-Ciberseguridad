**¿Qué son las variables de entorno?**

- Valores dinámicos que el sistema y las aplicaciones pueden usar    
- Evitan hardcodear rutas que pueden cambiar    
- Dos tipos: Sistema (global) y Usuario (per-user)
    
**¿Por qué existen?**

- Portabilidad: Scripts funcionan en diferentes PCs    
- Flexibilidad: Rutas pueden cambiar sin romper scripts    
- Seguridad: No exponer rutas sensibles en código    

**Ver todas las variables:**

- Get-ChildItem Env:    
- Get-ChildItem Env: | Sort-Object Name | Format-Table -AutoSize

Las variables se ponen con porcentaje % si se quieren utilizar desde interface grafica ejem
%SystemRoot%, para utilizarlas en consola seria 
```
En powershell
$env:NombreVariable

$env:PATH

Crea una variable
$env:Nombre = valor
```

# **Variables de entorno de Sistema**
**%SystemRoot%**
- Apunta a: C:\Windows    
- Por qué usarla: Windows podría estar en D:\Windows, E:\Windows    
- Ejemplo: %SystemRoot%\System32\cmd.exe siempre funciona  Poniendolo en el explorador de archivo como ruta  

**%SystemDrive%**
- Apunta a: C:    
- La unidad donde está instalado Windows    
- Normalmente C: pero no siempre    

**%ProgramFiles%**
- x64 systems: C:\Program Files (64-bit apps)    
- x86 systems: C:\Program Files    

**%ProgramFiles(x86)%**
- Solo en x64: C:\Program Files (x86) (32-bit apps)    
- No existe en sistemas de 32-bit

**%ProgramData%**
- **Apunta a:** C:\ProgramData    
- **Datos compartidos** entre usuarios    

**%TEMP% y %TMP% (Sistema)**
- **Apuntan a:** C:\Windows\Temp    
- **Archivos temporales** del sistema    
- **SYSTEM y servicios** escriben aquí

# **Variables de entorno Usuario**


**%UserProfile%**
- Apunta a: C:\Users\<username>    
- Raíz del perfil del usuario actual    
- Ejemplo de uso: %UserProfile%\Desktop para acceder al escritorio    

**%AppData%**
- Apunta a: C:\Users\<username>\AppData\Roaming    
- Datos de aplicaciones que roam    

**%LocalAppData%**
- Apunta a: C:\Users\<username>\AppData\Local    
- Datos locales que no roam
    

**%Temp% y %Tmp% (Usuario)**
- Apuntan a: C:\Users\<username>\AppData\Local\Temp    
- Archivos temporales del usuario    
- Aplicaciones del usuario escriben aquí (no en System Temp)