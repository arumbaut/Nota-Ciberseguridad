**INTEGRITY LEVELS**

**¿Qué son los niveles de integridad?**

Windows usa Integrity Levels para limitar qué procesos pueden escribir o modificar objetos del sistema. Funciona como una "jerarquía de confianza": un proceso con un nivel bajo no puede alterar objetos con un nivel más alto.

**Niveles principales:**
- **Low (Bajo)**    
    - Aislamiento fuerte. Usado por procesos potencialmente peligrosos (p. ej., sandboxes o IE Protected Mode).        
    - Solo lectura sobre niveles superiores.
        
- **Medium (Medio)**    
    - Nivel estándar de usuarios normales.        
    - Puede modificar objetos Medium y Low, pero no High.
    
- **High (Alto)**    
    - Procesos ejecutados con privilegios de administrador        
    - Pueden escribir en niveles High/Medium/Low        
- **System**    
    - Servicios críticos del sistema operativo (LocalSystem)        
    - Acceso completo, por encima incluso de High        
- **Protected Process / Protected Process Light (PPL)**    
    - Nivel especial para proteger antivirus, LSASS y componentes de seguridad        
    - Requiere firmas específicas; incluso administradores no pueden inyectar código

**¿Qué es UAC?**

UAC (User Account Control) es una característica de seguridad introducida en Windows Vista (y mejorada desde entonces) que separa los privilegios de usuario estándar de los privilegios administrativos.

**El problema que soluciona:**

Antes de Vista, en Windows XP, cuando iniciamos sesión como administrador, TODO lo que ejecutabas se ejecutaba con privilegios totales. Si hacías clic en un ejecutable malicioso, tenía privilegios de administrador automáticamente. Esto era un desastre de seguridad.

**La solución de UAC:**

Incluso si eres administrador, tu sesión por defecto se ejecuta con un token de acceso restringido (token filtrado). Solo cuando lo necesitas explícitamente, UAC te pide confirmación para "elevar" los privilegios.

A continuación, presento la extracción de texto de la imagen proporcionada (**image_f31829.png**) sobre los niveles de UAC en Windows:

En Windows hay 4 niveles de UAC (configurable desde el Panel de Control):

**Siempre notificar:**
- Te pide confirmación para TODO (aplicaciones y cambios del sistema)    
- Más seguro pero más molesto    
- El escritorio se atenúa (Secure Desktop)    

**Notificar solo cuando las aplicaciones intenten hacer cambios (por defecto):**
- Te avisa cuando programas externos quieren hacer cambios    
- NO te avisa para cambios que hagas tú en la configuración de Windows    
- Secure Desktop activado
    
**Igual que el anterior pero sin atenuar el escritorio:**
- Sin Secure Desktop (menos seguro, puede ser vulnerable a DLL hijacking)
    
**Nunca notificar:**
- UAC desactivado efectivamente    
- NO recomendado