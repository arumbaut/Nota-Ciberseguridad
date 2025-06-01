Los atacantes crean persistencia ejecutando código malicioso en el dispositivo objetivo al engañar a la víctima para que acceda a un archivo cargado de malware o descargue un programa malicioso. La persistencia permite a los atacantes infectar continuamente diferentes componentes del sistema y permanecer sin ser detectados frente a soluciones defensivas.

**Mantener la Persistencia Usando las Teclas de Fijación (Sticky Keys)**

En Windows, la función de Teclas de Fijación permite a los usuarios usar una combinación de teclas, como Ctrl, Alt y Shift, sin necesidad de presionarlas simultáneamente. Los atacantes pueden explotar esta función para mantener la persistencia.  

**Maintaining Persistence by Abusing Boot or Logon Autostart Executions**

Los atacantes aprovechan los programas de autoinicio del sistema durante el arranque o inicio de sesión para escalar privilegios y realizar ataques persistentes, aplicando configuraciones personalizadas en la máquina comprometida. Esta técnica permite a los atacantes ejecutar automáticamente un programa en el momento del arranque del sistema o al iniciar sesión.

**Listed below are the various techniques used by attackers to maintain domain dominance:**

**▪ Remote code execution:** Los atacantes intentan ejecutar código malicioso en el controlador de dominio (DC) objetivo a través de la línea de comandos (CLI) para lanzar un ataque de dominio dominante.

▪ Abusing the Data Protection API (DPAPI)

**▪ Malicious replication:** La replicación maliciosa permite a los atacantes crear una copia exacta de los datos del usuario utilizando credenciales de administrador.

**▪ Skeleton key attack:** ==Una _skeleton key_ es una forma de malware que los atacantes utilizan para inyectar credenciales falsas en los controladores de dominio (DCs), con el fin de crear una contraseña de puerta trasera.==

**▪ Golden ticket attack:** Un ataque de "golden ticket" es una técnica de post-explotación implementada por los atacantes para obtener control total sobre todo el **Active Directory (AD)**.

**▪ Silver ticket attack:** Un ataque de "silver ticket" es una técnica de post-explotación implementada por un atacante **para robar**  **las credenciales de usuarios legítimos y crear un ticket falso del Servicio de Concesión de Tickets (TGS)** de Kerberos.