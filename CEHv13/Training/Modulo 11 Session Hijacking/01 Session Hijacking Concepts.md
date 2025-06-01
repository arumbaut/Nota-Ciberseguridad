El secuestro de sesión (**session hijacking**) es un ataque en el que un atacante toma el control de una sesión de comunicación válida del **Protocolo de Control de Transmisión (TCP)** entre dos computadoras. Dado que la mayoría de los tipos de autenticación se realizan solo al inicio de una sesión TCP, un atacante puede obtener acceso a una máquina mientras la sesión está en curso. Un ataque de secuestro de sesión explota un mecanismo de generación de tokens de sesión o los controles de seguridad del token, de modo que el atacante pueda establecer una conexión no autorizada con un servidor objetivo. El atacante puede adivinar o robar un ID de sesión válido, que identifica a usuarios autenticados, y usarlo para establecer una sesión con el servidor. El servidor web responde a las solicitudes del atacante bajo la impresión de que está comunicándose con un usuario autenticado.

**Why is Session Hijacking Successful?**
▪ Absence of account lockout for invalid session IDs
▪ Weak session-ID generation algorithm or small session IDs
▪ Insecure handling of session IDs
▪ Ausencia de bloqueo de cuenta para IDs de sesión inválidos  
▪ Algoritmo débil de generación de IDs de sesión o uso de IDs de sesión demasiado cortos  
▪ Manejo inseguro de los IDs de sesión

**Session Hijacking Process**

![](attachments/image20250530131546.png)
**Session hijacking can be divided into three broad phases.**

**▪ Tracking the connection :** El atacante utiliza un network sniffer para rastrear a una víctima y al host, o emplea una herramienta como Nmap para escanear la red en busca de un objetivo con una secuencia TCP fácil de predecir.

**▪ Desynchronizing the connection :** Para desincronizar la conexión entre el objetivo y el host, el atacante debe modificar el número de secuencia o de reconocimiento (SEQ/ACK) del servidor. Para ello, el atacante envía datos nulos al servidor; como resultado, los números SEQ/ACK del servidor avanzan, mientras que la máquina objetivo no registra este incremento.

**▪ Injecting the attacker's packet:** El atacante inyecta datos en la red o participar activamente como intermediario (man-in-the-middle), transmitiendo datos del objetivo al servidor y viceversa, mientras lee e inyecta información a voluntad.