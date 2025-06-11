Qué cifrado fue seleccionado por el NIST como el **método principal para proporcionar confidencialidad** después del algoritmo **DES**

El **NIST seleccionó oficialmente el algoritmo AES** (basado en Rijndael) como reemplazo de DES debido a su seguridad, velocidad, eficiencia en hardware y software, y flexibilidad en tamaños de clave (128, 192, 256 bits).

¿Qué servicio en la nube es más probable que uses si deseas **compartir documentos con otra persona**?
Si tu objetivo principal es **compartir documentos**, el servicio **más adecuado y directo** es **Storage as a Service**, ya que está diseñado específicamente para almacenar y facilitar el acceso compartido a archivos en la nube.

¿Cuál es una de las ventajas de IPv6 sobre IPv4 desde una perspectiva de **seguridad**?

IPv6 permite la autenticación de encabezados.
La **ventaja clave de IPv6 en seguridad** es su **soporte integrado para IPsec**, que permite mecanismos de autenticación y cifrado directamente en el protocolo. Esto no es obligatorio en IPv4.

¿Qué algoritmo de cifrado es un **cifrado simétrico de flujo**?
RC4 es un **algoritmo de cifrado simétrico de flujo**
**ChaCha20**  y **Salsa20**  tambien son algoritmos simetricos de flujo

Eres el CISO de una gran empresa tecnológica. Estás encargado de implementar un cifrado para los nuevos dispositivos móviles que se lanzarán en 2022.  
¿Qué estándar de cifrado es el más probable que elijas?
**AES (Advanced Encryption Standard)** es la **mejor y más segura opción** para cifrar datos en dispositivos móviles. Es eficiente, confiable y ampliamente respaldado en estándares internacionales de seguridad

¿Cuál es la principal vulnerabilidad de una solicitud ARP?
La mayor vulnerabilidad de ARP es que **puede ser fácilmente suplantado (spoofed)**, permitiendo a un atacante insertar su dirección MAC para interceptar o manipular el tráfico de red.

La mayor vulnerabilidad de ARP es que **puede ser fácilmente suplantado (spoofed)**, permitiendo a un atacante insertar su dirección MAC para interceptar o manipular el tráfico de red.

¿Cuál es la ventaja de usar SSH para tráfico de línea de comandos?
SSH cifra el tráfico y las credenciales.

¿cuál es una de las fortalezas de clave registradas de RSA?
Las **fortalezas de clave comunes y registradas** para RSA son: **1024, 2048, 3072** y **4096 bits**.

Para proporcionar **no repudio** en el correo electrónico, ¿qué algoritmo elegirías implementar?
- El **no repudio** significa que el remitente **no puede negar** haber enviado un mensaje.    
- Para lograr no repudio, se necesita una **firma digital**, y para eso se utilizan algoritmos de **criptografía asimétrica**.    
- **DSA (Digital Signature Algorithm)** es un algoritmo específicamente diseñado para **firmas digitales** y es ampliamente utilizado para **proveer autenticidad e integridad**, así como no repudio.

¿Cuál de las siguientes opciones describe una **condición de carrera** (race condition)?
Cuando dos condiciones ocurren al mismo tiempo y existe la posibilidad de que se ejecuten comandos arbitrarios con permisos elevados del usuario, lo cual puede ser aprovechado por un adversario.

¿Por qué un atacante realizaría un escaneo de conexiones TCP abiertas usando Nmap?

- Un **escaneo TCP abierto (TCP Connect Scan)** realiza la conexión completa a los puertos, simulando tráfico legítimo de usuario porque establece una conexión completa.
    
- Esto puede **evitar ser detectado fácilmente por algunos sistemas de detección de intrusos**, haciendo que el escaneo parezca tráfico normal.

¿Cuál es un tipo común de ataque al protocolo Kerberos que puede parecer tráfico legítimo?
**Kerberoasting** es un ataque específico de Kerberos donde el atacante solicita tickets de servicio (TGS) legítimos para cuentas de servicio y luego intenta descifrar la contraseña almacenada en esos tickets fuera de línea.

¿Cuál de los siguientes forma parte de una DMZ pero sirve como puente de acceso entre organizaciones?
Una **extranet** es una red controlada que permite el acceso externo limitado a socios, proveedores o clientes de una organización. Suele estar ubicada en una **DMZ (zona desmilitarizada)**

¿Qué algoritmo de cifrado se utiliza dentro de TLS para el apretón de manos (handshake) y la negociación de claves?

**RSA (Rivest–Shamir–Adleman)** es un algoritmo de **cifrado asimétrico** que se utiliza comúnmente en el protocolo **TLS (Transport Layer Security)** durante la fase de **handshake** (apretón de manos) y **negociación de claves**.

¿La entrada del archivo de registro SAM se encuentra en qué parte del sistema de Registro de Windows?  
HKEY_LOCAL_MACHINE\SAM

¿Bajo qué módulo auxiliar en Metasploit se puede escanear configuraciones SNMP?

auxiliary/scanner/snmp

En **Metasploit**, los módulos auxiliares se organizan jerárquicamente por función.
### **Escaneo (Scanner)**
Estos módulos se utilizan para identificar sistemas, servicios y vulnerabilidades:

- `auxiliary/scanner/portscan/tcp`  
 Escanea puertos TCP abiertos en una máquina objetivo.
    
- `auxiliary/scanner/ftp/ftp_version`  
 Detecta la versión del servicio FTP.
    
- `auxiliary/scanner/snmp/snmp_enum`  
 Enumera información desde un dispositivo SNMP.
    
- `auxiliary/scanner/ssh/ssh_version`  
 Identifica la versión del servicio SSH.

### **Denegación de Servicio (DoS)**
- `auxiliary/dos/tcp/synflood`  
     Lanza un ataque SYN flood para saturar el sistema objetivo.

 Prueba entradas aleatorias o inesperadas para detectar fallos.
- `auxiliary/fuzzers/ftp/ftp_pre_post`  
 Prueba comandos FTP con cadenas anómalas para provocar errores.


¿Cuál es la región de memoria que se asigna a un proceso o programa cuando se inicia?
Stack

¿Qué estrategia utiliza un servidor DNS local con caché para buscar registros cuando se le consulta?
Recursive

¿Qué estándar promueve el proceso Planificar, Hacer, Verificar, Actuar (Plan, Do, Check, Act) para la implementación y validación de controles de seguridad?
 ISO 27001

¿Cómo se llama el software que crea mensajes de publicidad emergente (pop-up) mientras visitas sitios web?
. Adware

¿Cuál de las siguientes herramientas puede usarse para realizar un ataque DDoS a un sistema objetivo?
LOIC

En el modelo TCP/IP, ¿cuál es el equivalente de la capa de Red (Network) del modelo OSI?
Internet

**¿Cuál de las siguientes aplicaciones proporciona ARP spoofing?**
 Cain & Abel

**¿Qué opción describe a un adversario que finge ser otra persona para obtener crédito o intentar fraude?**
Identity theft (Robo de identidad)

**¿Cómo se refiere el modelo Clark-Wilson a los objetos cuando se trata de la integridad?**
UDI y CDI

**¿Qué modo inalámbrico se utiliza cuando hay una conexión punto a punto pero no hay un punto de acceso inalámbrico involucrado?**
Ad hoc

- El modo **Ad hoc** permite que dos o más dispositivos se conecten directamente entre sí sin necesidad de un punto de acceso inalámbrico (WAP).
    
- Es una conexión **punto a punto** o **peer-to-peer** en la que cada dispositivo actúa como cliente y servidor.

**¿Cuál es una ventaja de una llamada telefónica sobre un correo electrónico de phishing?**
You are able to go into more detail with pretexting using a conversation.

**¿Por qué es más probable que uses REST al desarrollar una aplicación web?**
HTTP is stateless.

¿Qué significa el valor TTL?
(El número de saltos restantes hasta que el paquete expire)

¿Cuál de los siguientes indica el servidor DNS autoritativo para la zona que se está consultando?
NS
- El registro **NS (Name Server)** en DNS identifica los servidores **autoritativos** para una zona o dominio específico.
    
- Estos servidores son responsables de responder con autoridad para los registros dentro de esa zona.

**Una clave que debe conocerse de antemano para poder cifrar datos entre dos partes se conoce como:**
 Pre-shared key (Clave precompartida)

Has encontrado un servidor SMTP abierto. ¿Qué comando SMTP podrías usar para identificar usuarios en ese servidor?
VRFY
El comando **VRFY** (Verify) permite consultar si un usuario específico existe en el servidor SMTP.

**¿Qué tipo de ataque es un ataque Fraggle?**
Amplification (Amplificación)

**¿Cuántos campos hay en un encabezado UDP?**
Four (Cuatro)

**¿Qué tipo de informe es mejor entregar al equipo de alta dirección de un cliente?**
Executive summary report**

**Como CISO, publicaste una política que requiere usar una trituradora de papel cruzada para destruir documentos clasificados de forma segura. ¿Qué tipo de control de seguridad implementaste?**
 Administrative (Administrativo)

**¿Cuál de los siguientes es el tipo de traducción de direcciones de red (NAT) más comúnmente usado?**
PAT (Port Address Translation)

**Si necesitas generar un código de autenticación de mensaje (MAC), ¿qué usarías?**
 SHA   
 Un **MAC (Message Authentication Code)** se genera usando funciones hash criptográficas combinadas con una clave secreta.
 
**Si quisieras usar un plugin de navegador para identificar las tecnologías usadas en un sitio web, ¿cuál usarías?**
 Wappalyzer
 **Wappalyzer** es un plugin popular que detecta y muestra las tecnologías que usa un sitio web, como frameworks, servidores, CMS, bibliotecas JavaScript, etc

**¿Qué tipo de ICMP indica una respuesta "Time Exceeded"?**
 Type 11

**Cuál de los siguientes es un protocolo propietario ligero de Cisco para construir túneles de seguridad?**
 LEAP
 **LEAP (Lightweight Extensible Authentication Protocol)** es un protocolo propietario de Cisco diseñado para autenticación segura y construcción de túneles en redes inalámbricas.

**¿Qué usan los puntos de acceso inalámbricos para anunciar su presencia?**
 Beacon frame
 Los **Beacon frames** son paquetes periódicos enviados por los puntos de acceso (AP) para anunciar la existencia de la red inalámbrica, incluyendo información como el SSID, capacidades, y parámetros de la red.