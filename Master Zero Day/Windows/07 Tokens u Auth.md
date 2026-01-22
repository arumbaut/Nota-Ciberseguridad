**ACCESS TOKEN**

**¿Qué es un Access Token?**
- Cuando inicias sesión en Windows, el sistema crea un Access Token para tu sesión. Este actúa como tu "badge de identidad" que llevas con cada acción que realizas.    
- LSASS durante logon
    

**Contenido de un Access Token**
- SID del usuario    
- SIDs de todos los grupos a los que perteneces (incluidos grupos anidados)    
- Privilegios asignados (ej. SeDebugPrivilege, SeBackupPrivilege)    
- Sesión Logon ID    
- Integrity Level (Low, Medium, High, System)    
- Flags (ej. si es elevado, si es restringido)
    

**Tipos de tokens**
- **Primary Token:** Asociado a un proceso principal    
- **Impersonation Token:** Un proceso actúa temporalmente como otro usuario

**PRIVILEGIOS**

Los privilegios son capacidades especiales más allá de los permisos normales:
- **SeDebugPrivilege:** Depurar procesos (incluso de otros usuarios)    
- **SeBackupPrivilege:** Hacer backup de archivos (ignorando permisos NTFS)    
- **SeRestorePrivilege:** Restaurar archivos    
- **SeShutdownPrivilege:** Apagar el sistema    
- **SeTakeOwnershipPrivilege:** Tomar posesión de objetos    
- **SeLoadDriverPrivilege:** Cargar drivers de kernel    
- **SeImpersonatePrivilege:** Suplantar a otro usuario
    

**Integrity Levels**
- Los niveles de integridad evitan que procesos de bajo privilegio modifiquen objetos de mayor privilegio.    
- Un proceso con nivel bajo NO puede modificar objetos de nivel medio o superior.


**NTLM AUTH**

**¿Qué es NTLM?**
NTLM es el protocolo de autenticación heredado de Windows NT. Aunque es antiguo (de los 90), todavía se usa en:
- Equipos en workgroup (sin dominio)    
- Autenticación fallback cuando Kerberos no está disponible    
- Algunos servicios legacy    
- Autenticación con direcciones IP en lugar de nombres

**PROTOCOLO SMB**

**¿Qué es SMB?** SMB (Server Message Block) es el protocolo que Windows usa para:
- Compartir archivos en red    
- Compartir impresoras    
- Comunicación entre procesos (named pipes)    

**Versiones de SMB**
- **SMB 1.0:** Antiguo, INSEGURO, deshabilitar siempre (vulnerable a WannaCry, EternalBlue)    
- **SMB 2.0:** Introducido en Windows Vista/Server 2008    
- **SMB 2.1:** Windows 7/Server 2008 R2    
- **SMB 3.0:** Windows 8/Server 2012 (soporta cifrado)    
- **SMB 3.1.1:** Windows 10/Server 2016 (mejoras de seguridad y performance)    

**SMB y autenticación** Cuando accedes a un recurso compartido (`\\SERVER\share`):
- SMB negocia la versión del protocolo    
- En dominio: Prefiere Kerberos (SPN = CIFS/SERVER)    
- Sin dominio o fallback: Usa NTLM    

Una vez autenticado, SMB permite acceso según permisos

**NTLM AUTH**

**Cómo funciona NTLM (Challenge-Response)**
El proceso de autenticación NTLM funciona así:

**Cliente solicita acceso al servidor**
- Cliente: "Quiero acceder a \SERVER\recurso como DOMINIO\usuario"    

**Servidor envía un Challenge (desafío)**
- Servidor: "OK, aquí tienes un número aleatorio: [challenge de 8 bytes]"    

**Cliente cifra el challenge con el hash de su contraseña**
- Cliente calcula: NTLM_Response = función(hash_contraseña, challenge)    
- Cliente envía: [usuario, dominio, NTLM_Response]    

**Servidor valida la respuesta**
- Si es autenticación local: El servidor tiene el hash en su SAM y puede validarlo directamente  
- Si es autenticación de dominio: El servidor reenvía todo al Domain Controller (Netlogon service), y el DC valida usando su copia del hash    

**Resultado**
- Servidor: "OK, autenticado" o "Acceso denegado"


**Versiones de NTLM**

- **NTLMv1:** Muy inseguro, vulnerable a rainbow tables y relay attacks    
- **NTLMv2:** Más seguro, usa challenge más largo y cifrado más fuerte    
- **Recomendación:** Deshabilitar NTLMv1 completamente
    

**Problemas de NTLM**
- **No mutual authentication:** El cliente no verifica la identidad del servidor (vulnerable a ataques man-in-the-middle)    
- **Vulnerable a relay attacks:** Un atacante puede capturar y retransmitir la respuesta NTLM    
- **Menos eficiente:** Cada autenticación requiere comunicación con el DC


**¿Qué es Kerberos?**

Kerberos es el protocolo de autenticación moderno usado en Active Directory desde Windows 2000. Su nombre viene del perro de tres cabezas de la mitología griega (Cerbero).

**Ventajas sobre NTLM:**
- **Mutual authentication (el cliente verifica al servidor)**    
- **Más rápido (usa tickets, no requiere contactar al DC en cada autenticación)**    
- **Soporta delegación**    
- **Más seguro criptográficamente**


**KERBEROS AUTH**

**Componentes de Kerberos**
**KDC (Key Distribution Center):**
Servicio que se ejecuta en los Domain Controllers. Tiene dos componentes:
- **AS (Authentication Service):** Emite TGTs    
- **TGS (Ticket Granting Service):** Emite Service Tickets   

**Tickets:**
- **TGT (Ticket Granting Ticket):** Prueba de que estás autenticado    
- **TGS (Ticket Granting Service):** Permite acceder a un servicio específico   

**Principals:**
- **User Principal:** Un usuario (ej. usuario@DOMINIO.COM)    
- **Service Principal (SPN):** Un servicio (ej. HTTP/servidor.dominio.com)