## 🧠 **1. Información del sistema**

`systeminfo`

- Muestra versión de Windows, parches, arquitectura (útil para detectar exploits posibles).
    

`hostname`

- Muestra el nombre del equipo (útil para moverse por la red).
    

`whoami`

- Muestra el usuario actual (importante para verificar privilegios).
    

`echo %username%`

- Muestra el nombre de usuario actual (variante de `whoami`).
    

`set`

- Muestra variables de entorno, rutas, y datos interesantes.
    

---

## 🧭 **2. Enumeración de red**

`ipconfig /all`

- Muestra interfaces de red, DNS, gateways, etc.
    

`netstat -ano`

- Muestra conexiones de red activas con PID (útil para detectar shells, backdoors, C2).
    

`arp -a`

- Muestra tabla ARP (otros hosts en red local).
    

`net view /domain`

- Enumera equipos en el dominio o red.
    

`net view \\nombre_o_ip`

- Muestra recursos compartidos de un host.
    

---

## 👤 **3. Usuarios y grupos**

`net user`

- Lista usuarios locales.
    

`net user <nombre>`

- Muestra detalles del usuario (último login, grupos, etc).
    

`net localgroup`

- Muestra los grupos del sistema.
    

`net localgroup Administrators`

- Enumera los miembros del grupo de administradores.
    

---

## 🔒 **4. Control de procesos y servicios**

`tasklist`

- Muestra procesos en ejecución.
    

`taskkill /F /PID <id>`

- Mata un proceso por su ID.
    

`sc query`

- Lista todos los servicios.
    

`sc qc <servicio>`

- Muestra configuración de un servicio (ruta, permisos).
    

`wmic process list brief`

- Alternativa para ver procesos con más info.
    

---

## 📂 **5. Archivos y rutas**

`dir /s /b`

- Muestra todos los archivos y rutas completas (útil para buscar credenciales, backups, etc).
    

`tree /f`

- Muestra estructura completa de carpetas.
    

`type archivo.txt`

- Muestra el contenido de un archivo.
    

`attrib -h -s archivo.txt`

- Elimina atributos oculto/sistema (útil para ver archivos escondidos).
    

---

## 🧱 **6. Escalación y persistencia**

`at`

- Tareas programadas (más usado en Windows antiguos).
    

`schtasks /query /fo LIST /v`

- Tareas programadas detalladas (útil para backdoors persistentes).
    

`reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run`

- Persiste ejecutando algo en cada reinicio.
    

`whoami /priv`

- Verifica privilegios (como `SeDebugPrivilege`, útil para escalación).
    

---

## 🛠️ **7. Herramientas ocultas y útiles**

`powershell`

- Entras a PowerShell (mucho más poderoso que CMD).
    

`cmdkey /list`

- Lista credenciales almacenadas (muy útil para robo o movimiento lateral).
    

`runas /user:<dominio\usuario> cmd`

- Ejecuta comandos como otro usuario (si tienes sus creds).
    

`cipher /w:C:\`

- Borra archivos eliminados (wipespace) — útil para **limpiar rastros**.
    

---

## 📌 BONUS: Comandos útiles para evasión o stealth

`@echo off`

- Oculta comandos en scripts por lotes.
    

`copy con archivo.bat`

- Crea scripts rápido desde CMD.
    

`for /F %i in ('dir /b /s *.config') do type %i`

- Busca y lee todos los archivos `.config`, útil para encontrar contraseñas.
    

---

## 🔚 Resumen

|Área|Comando clave|
|---|---|
|Info del sistema|`systeminfo`, `whoami`|
|Red|`ipconfig`, `netstat`, `net view`|
|Usuarios/grupos|`net user`, `net localgroup`|
|Procesos/servicios|`tasklist`, `sc`, `wmic`|
|Archivos|`dir /s /b`, `type`|
|Persistencia|`schtasks`, `reg query`|
|Powershell|`cmdkey`, `runas`|

---

¿Quieres que te dé un **script por lotes (batch)** que automatice algunos de estos comandos para usarlos en post-explotación?

```
@echo off
echo [+] Iniciando recolección de información...
set OUTPUT=post_exploit_%COMPUTERNAME%.txt

echo ========================= >> %OUTPUT%
echo SYSTEM INFO >> %OUTPUT%
echo ========================= >> %OUTPUT%
systeminfo >> %OUTPUT%
hostname >> %OUTPUT%
whoami /all >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo NETWORK INFO >> %OUTPUT%
echo ========================= >> %OUTPUT%
ipconfig /all >> %OUTPUT%
arp -a >> %OUTPUT%
netstat -ano >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo USERS & GROUPS >> %OUTPUT%
echo ========================= >> %OUTPUT%
net user >> %OUTPUT%
net localgroup >> %OUTPUT%
net localgroup Administrators >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo RUNNING TASKS & SERVICES >> %OUTPUT%
echo ========================= >> %OUTPUT%
tasklist >> %OUTPUT%
sc query >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo SCHEDULED TASKS >> %OUTPUT%
echo ========================= >> %OUTPUT%
schtasks /query /fo LIST /v >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo REGISTRY RUN KEYS (Persistence) >> %OUTPUT%
echo ========================= >> %OUTPUT%
reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run >> %OUTPUT%
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run >> %OUTPUT%
echo. >> %OUTPUT%

echo ========================= >> %OUTPUT%
echo CREDENCIALES GUARDADAS >> %OUTPUT%
echo ========================= >> %OUTPUT%
cmdkey /list >> %OUTPUT%
echo. >> %OUTPUT%

echo [+] Recolección finalizada. Resultado en: %OUTPUT%
pause

```