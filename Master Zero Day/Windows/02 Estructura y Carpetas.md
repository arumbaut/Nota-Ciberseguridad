**Carpetas del Sistema**

- **C:\Windows - La Raíz del Sistema Operativo**    
- **C:\Windows\System32 - La Carpeta Más Importante**    
    - La gran confusión del nombre:        
    - En Windows 64-bit, System32 contiene binarios de 64 bits, NO de 32 bits        
    - Sí, leíste bien. System32 = 64-bit en sistemas x64
        
    - Contiene:        
        - Todos los ejecutables críticos del sistema: cmd.exe, notepad.exe, regedit.exe            
        - DLLs del sistema: kernel32.dll, user32.dll, ntdll.dll            
        - Herramientas administrativas: mmc.exe, services.msc            
        - Drivers: subdirectorio drivers\ con archivos .sys
            
- **C:\Windows\SysWOW64 - Windows on Windows 64**    
    - WOW64 = Windows on Windows 64-bit        
    - Subsistema de emulación que permite ejecutar apps de 32-bit en Windows de 64-bit
        
- **C:\ProgramData**    
    - Datos de aplicaciones compartidos entre TODOS los usuarios        
    - Configuraciones globales de programas        
    - Bases de datos, logs, caches de aplicaciones
    
- **C:\Program Files:** En sistemas x64: Aplicaciones de 64 bits se instalan aquí.
    
- **C:\Program Files (x86):** Solo en Windows x64: Aplicaciones de 32 bits se instalan aquí.
    
- **AppData:**    
    - **AppData\Roaming:** Configuraciones de aplicaciones que quieres en todos tus PCs.        
    - **AppData\Local:** Datos locales que NO deben sincronizarse como las caches.        
    - **AppData\LocalLow:** Datos para aplicaciones con integrity level BAJO.
        
- **C:\Users<username>\ - Carpeta de usuario:** Desktop, Documents, Pictures, Videos, Music, Downloads.
    
- **C:\Users\Public:** Compartir archivos entre TODOS los usuarios del PC. Cualquier usuario puede leer y escribir aquí.