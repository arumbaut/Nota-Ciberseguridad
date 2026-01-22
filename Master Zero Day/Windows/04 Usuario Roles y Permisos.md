**Cuentas Locales**

Las cuentas locales son las que están almacenadas directamente en el equipo. Cuando instaláis Windows en vuestro portátil o PC de casa y creáis un usuario, estáis creando una cuenta local. Estas cuentas:

- Se almacenan en una base de datos local llamada **SAM (Security Accounts Manager)**    
- La base de datos SAM está ubicada en **C:\Windows\System32\config\SAM**    
- Solo sirven para autenticarse en **ESE** equipo específico    
- Las credenciales (hash de la contraseña) están cifradas y guardadas localmente    
- No se sincronizan con otros equipos
    
**Cuentas locales importantes que vienen por defecto:**

- **Administrator:** La cuenta con más privilegios del sistema. Por defecto viene deshabilitada desde Windows Vista por seguridad, pero existe.    
- **Guest:** Una cuenta de invitado con privilegios muy limitados.    
- **DefaultAccount:** Usada por el sistema para ciertos procesos.    
- **WDAGUtilityAccount:** Relacionada con Windows Defender Application Guard.

```
whoami

Muestra todos los user
net users
```

**CUENTAS LOCALES VS. CUENTAS DE DOMINIO**

**Cuentas de Dominio (Active Directory)**

Ahora, las cuentas de dominio son completamente diferentes.
- Se crean y almacenan en un Active Directory Domain Controller (servidor de dominio)    
- Permiten autenticarse en CUALQUIER equipo que esté unido al dominio    
- Las credenciales se validan contra el controlador de dominio, no localmente    
- Permiten políticas centralizadas (Group Policy)    
- El formato típico es DOMINIO\usuario o usuario@dominio.com    

**Ventajas de las cuentas de dominio:**
- **Single Sign-On (SSO):** te auténticas una vez y accedes a múltiples recursos    
- **Gestión centralizada:** el administrador gestiona todo desde un solo lugar    
- **Políticas de grupo:** configuraciones que se aplican automáticamente    
- **Escalabilidad:** puedes tener miles de usuarios gestionados centralmente

**SID - SECURITY IDENTIFIER**

**¿Qué es un SID?**
Un SID es un identificador único que Windows asigna a cada security principal. ¿Qué es un security principal? Cualquier entidad que pueda ser autenticada: un usuario, un grupo, un equipo, incluso servicios.

Lo importante: Windows NO identifica a los usuarios por su nombre. Los nombres son para humanos. Internamente, Windows usa los SIDs.

**S - 1 - 5 - 21-3623811015-3361044348-30300820 - 1013**
- **S:** Indica que es un SID (siempre es S)    
- **Revision:** Siempre es 1 (versión de la especificación SID)    
- **Authority:** Identifica la autoridad que emitió el SID    
    - 5 = NT Authority (lo más común)        
    - 1 = World Authority        
    - 2 = Local Authority        
- **Sub-authorities:** Serie de números que identifican el dominio o máquina    
- **RID (Relative Identifier):** El último número, identifica el objeto específico dentro del dominio/máquina
    
    - Los RIDs por debajo de 1000 están reservados para cuentas y grupos del sistema. Los usuarios empiezan en 1000 o superior.

**SIDs conocidos (Well-Known SIDs)**
- [https://learn.microsoft.com/es-es/windows/win32/secauthz/well-known-sids](https://learn.microsoft.com/es-es/windows/win32/secauthz/well-known-sids)
    
**¿Por qué son importantes los SIDs?**
- **Seguridad robusta:** Aunque cambiéis el nombre de un usuario, su SID no cambia. Los permisos están asociados al SID.    
- **Imposible de falsificar:** Son generados criptográficamente. Dos equipos diferentes NUNCA generarán el mismo SID.    
- **Auditoría y forense:** En los logs de eventos, todo se registra con SIDs, no con nombres de usuario.