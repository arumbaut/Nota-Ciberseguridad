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

¿Cuál de los siguientes algoritmos de cifrado utiliza dos números primos grandes?
RSA. El algoritmo **RSA**  **se basa en la factorización de dos números primos grandes**.

¿Qué características de protección se utilizan con el modo de transporte de IPSec?
#### **Proporciona cifrado solo a la carga útil**    
- En **modo transporte **, **solo se cifra la carga útil**, no la cabecera
- El modo tunel cifra ambos ip header o cabecera y el payload

¿Cuál de los siguientes define los rangos de direcciones IP privadas, no enrutable por Internet?
RFC 1918.  Este **RFC** (Request for Comments) define los rangos de direcciones IP **privadas** que **no son enrutable por Internet**.

Cuando intentas cambiar la URL a otro formato que podría no ser bloqueado por el firewall, como binario. ¿Qué estás intentando hacer?
URL obfuscation (Ofuscación de URL)

¿Qué rango de tamaño de clave utiliza RC4 dentro del protocolo WEP?
40 to 256 bits

¿Cuántas etapas se usan en el apretón de manos (handshake) para establecer credenciales en WPA/2/3?
Cuatro

En Kerberos, ¿qué ticket se presenta a un servidor para obtener acceso a un servicio?
TGT 

¿Cuántas técnicas diferentes podrías usar para escanear puertos UDP abiertos?
1

¿Qué herramienta puedes usar en un sistema Windows para recopilar información sobre la red de Windows, incluyendo el grupo de trabajo o dominio al que estás conectado?
nbtstat  
nbtstat muestra información sobre la caché de nombres NetBIOS, el estado de las conexiones NetBIOS, y puede mostrar información sobre grupos de trabajo o dominios a los que está conectado el equipo Windows.

¿En qué etapa dentro de Kerberos se autentica el sujeto (usuario)?
**La autenticación del sujeto (usuario o cliente) ocurre cuando el cliente recibe el TGT (Ticket Granting Ticket)**, que es emitido por el **AS (Authentication Server)**

¿Qué método no convencional usarías para provocar una denegación de servicio (DoS) en toda la sala?
Atacar las unidades HVAC (calefacción, ventilación y aire acondicionado).

¿Qué herramienta usarías para buscar código de exploits de prueba de concepto en un sistema como Kali o ParrotOS?
Searchsploit

¿Para cuál de estas tareas NO usarías el sitio web Shodan?
Identificar rangos de direcciones IP de una empresa   duda Identificar contraseñas por defecto en Internet

¿Qué cifrado de rotación usa una matriz para mapear texto cifrado a texto plano y viceversa?
El **cifrado Vigenère** es un cifrado polialfabético que usa una **matriz de tabula recta (tabla Vigenère)**

¿Quién tiene la responsabilidad del sistema operativo en una oferta de Plataforma como Servicio (PaaS) con un proveedor de la nube?
Proveedor

¿Cuál de estas sería una vulnerabilidad muy común en implementaciones de computación en la nube que podría llevar a la explotación?
Gestión débil de acceso

¿Qué técnica podría usar un autor de malware que sería más efectiva para evadir la detección por software antimalware?
Polimorfismo

¿Cuál de estas tecnologías usarías para eliminar malware en la red antes de que llegue al endpoint?
Dispositivo de gestión unificada de amenazas (UTM)
Un **UTM es un dispositivo que integra múltiples funciones de seguridad de red, como firewall, antivirus, detección de intrusos, filtrado web y análisis de malware.

¿Cuál de estas utilidades usarías para capturar contraseñas desde el Registro del sistema así como desde la memoria de un sistema comprometido?
**Mimikatz** . Esta es una herramienta muy conocida para extraer credenciales (contraseñas, hashes, tickets) directamente de la memoria y del sistema Windows, incluyendo del proceso **LSASS**

¿Qué técnica podría ser la más efectiva para comprometer un dispositivo móvil?
Tienda de aplicaciones

¿Cuál de estos ataques sería menos probable que tenga éxito contra una aplicación web en una arquitectura cloud-native?
SQL injection

¿Qué flag se usa para terminar una conexión que está solo parcialmente abierta?
RST

¿Qué proporcionan los flujos de datos alternativos (Alternate Data Streams) en NTFS?
Pueden ocultar un archivo detrás de otro archivo.

¿Qué protocolo usarías con mayor probabilidad para que un sistema en tu red local te envíe tráfico que debería enviarse a otro sistema?
ARP

¿Qué configuración de servidor agrupa varios servidores y proporciona redundancia y tolerancia a fallos?
Clustering

¿Qué tipo de etiqueta se le da a un sujeto por razones de seguridad?
Clearance.
**Clearance (Autorización)** es la etiqueta o nivel que se asigna a una persona (sujeto) que indica a qué información clasificada puede acceder.

¿Qué necesitas activar en una interfaz de red para poder ver las cabeceras de radio en la comunicación?
Monitor mode

¿Qué modo en una interfaz de red es necesario para capturar tráfico?
Promiscuous mode

¿Qué llave se usa para cifrar mensajes dirigidos al dueño de un certificado cuando se usa cifrado asimétrico?
Llave pública

¿Cuál de los siguientes ataques usa paquetes UDP para atacar la dirección de broadcast y causar un DDoS?
Fraggle
**Fraggle** usa **paquetes UDP** (en lugar de ICMP como el Smurf) enviados a la dirección de broadcast para amplificar el ataque y causar un DDoS.

¿Qué herramienta provoca que se usen todos los sockets y puede hacer que los servicios se congelen o caigan?
**Slowloris**.  Es un ataque DoS que abre muchas conexiones HTTP lentas, manteniendo abiertas las conexiones sin completar.

¿Cómo se llama el dispositivo simple que se usa para gestionar los elementos de nivel más bajo de un sistema de control industrial?
Programmable logic controller (PLC)

¿Qué es una plataforma informática que ofrece una solución alojada por un proveedor de servicios, sobre la cual los clientes pueden construir aplicaciones?
Platform as a Service (PaaS)

¿Qué protocolo tiene soporte nativo para IPSec?
IPv6

¿En qué capa opera ICMP?   Layer 3 (Capa 3)

¿Cuál es una forma sencilla de obtener credenciales de usuarios inalámbricos?
Evil twin

¿Por qué la aleatorización del espacio de direcciones (ASLR) es efectiva contra los ataques de desbordamiento de búfer?
La dirección de retorno cambia constantemente

¿Qué protocolo utiliza el exploit EternalBlue?
SMB (Server Message Block)

¿Por qué usaría un atacante un troyano?
Para lograr que un usuario lo ejecute

¿Cuál de las siguientes aplicaciones te permite descifrar contraseñas WEP en una red inalámbrica?
Cain & Abel.
**Cain & Abel** es una herramienta de recuperación de contraseñas para sistemas Windows, que incluye funciones como: Escucha de tráfico de red, Ataques de diccionario y fuerza bruta,
**Crackeo de claves WEP**, si se captura suficiente tráfico.

¿Qué herramienta podrías usar si quisieras identificar directorios que no aparecen en el escaneo (spider) de un sitio web?
- **DIRB**  Esta una herramienta de **fuerza bruta para descubrir directorios y archivos ocultos** en servidores web.

¿Qué herramienta podrías usar para ayudarte a capturar cabeceras de radio en redes inalámbricas?
Airmon-ng

Encuentras el ejecutable `fping` en un sistema. ¿Qué es lo que probablemente estaba haciendo alguien?
Ping sweeps

Con Plataforma como Servicio (PaaS), ¿de cuál de estos elementos _no_ serías responsable como consumidor del servicio?
Operating system

¿Cuál de los siguientes algoritmos implementó con éxito el sistema criptográfico de clave pública?
RSA

¿Dónde irías para obtener el nombre y la información de contacto del administrador de un dominio?
**RIR (Regional Internet Registry)** son organizaciones que administran la asignación de direcciones IP y mantienen bases de datos públicas con información del propietario y contacto de esas direcciones, incluyendo a veces datos de dominios relacionados.

Cómo se llama un mensaje que lleva datos y acuses de recibo (acknowledgments)?
Segment. Un **segmento** es la unidad de datos en la **capa de transporte (TCP)**.

Has localizado un servidor RMI en una red objetivo. ¿Qué información te gustaría obtener de ese servidor?
Applications being hosted
Un **servidor RMI (Remote Method Invocation)** permite que aplicaciones Java invocan métodos remotamente en otro sistema

¿Qué hace un puntero de pila (stack pointer)?
Apunta a la cima (tope) de la pila.

En el escaneo de virus, ¿cuál es la señal característica que indica la presencia de un virus?
Firma (signature)

¿Qué es lo que un escáner de vulnerabilidades como Nessus no utiliza para identificar vulnerabilidades?
Exploited service

En Linux, ¿qué método usa un esfuerzo de fuerza bruta para localizar un archivo?
find

¿Cuál de los siguientes no podrías acceder usando un ataque de inyección de entidad externa XML (XXE)?
Cookie del usuario desde el navegador

Como hacker ético (white hat), tu cliente te pregunta qué tipos de evaluaciones puedes realizar. ¿Cuáles son?
Riesgo, amenaza y vulnerabilidad

Un método que defiende contra ataques de inundación (flooding) y ataques masivos de DoS se conoce como qué?
Flood guard.  Esta es una tecnología o método diseñado específicamente para detectar y prevenir ataques de inundación (flooding)

En IPSec, ¿qué se conoce como el gestor de asociaciones de seguridad?
**ISAKMP (Internet Security Association and Key Management Protocol)** es el protocolo que se encarga de gestionar la creación, negociación y mantenimiento de las asociaciones de seguridad (Security Associations, SA) en IPSec.

El acto de falsificar datos también se conoce como qué?
**Spoofing**

Cuando las aplicaciones crean segmentos de memoria variable de forma dinámica, ¿qué tipo de memoria están usando?
Heap

**Este fragmento se encuentra en los registros de un servidor web. ¿Qué tipo de ataque es probable que esté ocurriendo?**  
`&& cat /etc/shadow`

Command injection

¿Cuál es un identificador único que se usa en Snort?
SID **(Snort ID)**.

¿Cuál de las siguientes herramientas puede usarse para robar cookies entre un cliente y un servidor para usar en un ataque de repetición (replay attack)?
**Ferret** es una herramienta diseñada para capturar datos de sesiones HTTP, incluyendo cookies, en redes no cifradas, lo que permite a un atacante realizar ataques de repetición (replay attacks) usando esas cookies robadas.

DNS Caché snooping es un tipo de enumeracion DNS en la cual un atacante hace peticiones a un servidor de un registro especifico del DNS. Por medio de el caché record el atacante uede determinar visitas recientes de los usuarion. 
Que comando es usado para determinar si la entrada esta presente en la cache DNS
nslookup -norecurse www.ABCompany.com

¿Cuál de las siguientes es otro nombre para la sobrecarga de NAT?
PAT

¿Cuál de los siguientes es parte de la porción general del SID?
The resource identifier (RID)

¿Cuál es la longitud de la clave de cifrado en DES?
56

¿Cuál de los siguientes te permite buscar rápidamente sitios web vulnerables a inyecciones SQL?
Google Dorks

¿Cuál es el RID de la cuenta de invitado (Guest) en un sistema Windows?
RID 501

Cuando se intenta identificar todas las estaciones de trabajo que responden en una subred, ¿cuál es el método más rápido que podrías elegir?
Barrido de ping (Ping sweep)

En Snort, ¿qué tipo de regla permite notificación solo si hay una coincidencia?
Alert

¿Qué tipo de control es un firewall?
Lógico

¿Cómo se llama el proceso de intentar inyectar entradas falsas en la tabla ARP?
Envenenamiento ARP (ARP poisoning)

¿Qué directorio contiene los comandos básicos en Linux?
/bin

Un atacante disfrazado de empleado postal, con cajas grandes, sigue a un grupo de trabajadores para entrar por la parte trasera de la instalación. ¿Qué tipo de ataque está intentando?
Piggybacking

¿Qué elemento del sistema se utiliza para almacenar información y es instalado por el servidor web?
Cookies

Estás caminando por el centro recogiendo puntos de acceso inalámbricos abiertos. Cuando los identificas, colocas un símbolo en un edificio cercano. ¿Qué actividad estás realizando?
Warchalking

¿Qué tipo de virus puede cambiar o reescribirse cada vez que infecta un archivo nuevo?
Virus metamórfico

¿Qué algoritmo de hash fue desarrollado por la NSA y tiene una salida de 160 bits?
SHA-1

¿Qué herramienta tiene más sentido usar para identificar dispositivos IoT en una red?
Nmap

¿Cómo establecería un administrador una contraseña para un usuario en Linux?
passwd user

En Windows, ¿cuál es el comando para mostrar la caché ARP?
arp -a

¿Cuál es la segunda fase en la metodología del hacking ético?
Escaneo

¿Qué sitio puedes usar para buscar en una base de datos de vulnerabilidades?
nvd.nist.gov

Como analista de negocios, estudias y recopilas información sobre tu competencia usando Google, su sitio web y productos. ¿Cuál de las siguientes opciones define mejor lo que estás haciendo?
Inteligencia competitiva

¿Cuál de los siguientes transmite en texto plano las cadenas de comunidad como método de autenticación?
SNMPv1

Una cajera del banco necesita la autorización del gerente para retirar una gran suma de dinero para un cliente. Sin el gerente, no puede hacerlo. ¿Qué tipo de control de acceso se está aplicando en este caso?Separación de funciones

¿De qué se aprovecha un exploit dentro de un sistema o red?
Una vulnerabilidad

¿Por qué usarías un diseño RESTful en tu aplicación web?
HTTP es sin estado

¿Qué información debe conocerse para que un cliente inalámbrico se conecte a un punto de acceso y pueda acceder o ser desafiado con autenticación?
SSID

¿Qué debe tener un usuario para capturar (sniff) todo el tráfico de la pila completa inalámbrica?
Dispositivo inalámbrico en modo monitor

Tu empresa ha sido objetivo de una serie de correos electrónicos de phishing. Para evitar el ataque, indicas rápidamente a los usuarios que verifiquen a los remitentes. ¿Cómo implementas esto? 
Asegurar que el correo esté firmado digitalmente

¿Qué oferta de nube otorga al cliente la mayor responsabilidad?
Infraestructura como Servicio (IaaS)

¿Qué tipo de malware puede usarse para proporcionar acceso backdoor a un sistema?
Rootkit

¿Qué comando establece una sesión nula (null session) en Windows?
net use \yourdomain\ipc$ "" /u: ""

Convertir código binario a una cadena ASCII reversible se logra mediante qué método?
Usando codificación Base64

¿Cuál de los siguientes se puede usar para detectar señales inalámbricas?
AirCheck

Un atacante usa un motor de búsqueda para localizar sitios web posiblemente vulnerables a inyecciones SQL utilizando palabras clave especiales conocidas por el motor de búsqueda. ¿Qué motor de búsqueda usaría más probablemente?
Google

Un supervisor sospecha que se están realizando actividades fraudulentas en el lugar de trabajo. ¿Qué opción puede usar para confirmar su sospecha?
Vacaciones forzadas

Si un usuario quiere cifrar información usando cifrado asimétrico para que las claves no tengan que compartirse abiertamente, ¿qué usaría?
La clave pública del receptor

¿Qué registro indica la asignación de una dirección IP a un nombre de host?
PTR

**¿Qué valor se usa en asociación con firewalking?**
A. TTL 

¿Por qué un atacante preferiría usar bluesnarfing en lugar de bluejacking?
Bluejacking envía mientras que bluesnarfing recibe

¿Qué método permitiría a un administrador reducir la amenaza de envenenamiento DNS?
Aumentar la tasa de actualización

¿Qué clave se incluye en un certificado digital?
La clave pública está almacenada en el certificado.

¿Qué tipo de escaneo usarías para mapear reglas de firewall?
ACK

¿Cuál de estas no sería una razón para usar automatización en un entorno en la nube?
Tolerancia a fallos.  Porque la tolerancia a fallos es una característica del diseño del sistema, no directamente una razón para usar automatización.

Si estuvieras moviendo tu infraestructura TI de local a un proveedor de servicios en la nube, ¿qué podría preocuparte más que sea diferente a lo que ya tienes?
Imposibilidad de implementar controles de seguridad

¿Cuál de los siguientes servidores AAA proporciona cifrado asimétrico?
SESAME

**¿Cuál de los siguientes no es un objeto en Active Directory?**
Archivos 

¿Cuál de las siguientes herramientas utiliza Metasploit para lanzar ataques como campañas de phishing?
Setoolkit

¿Qué herramienta podrías usar para descubrir vulnerabilidades previamente desconocidas en un servicio de red o aplicación local?
Peach. Porque Peach es una herramienta de fuzzing que ayuda a encontrar vulnerabilidades desconocidas enviando datos inesperados.

¿Cuál de los siguientes informará al usuario que el puerto está cerrado por el cliente mismo?
ICMP Tipo 3, Código 3

¿Cuál de las siguientes capas en el modelo OSI contiene la capa de Transporte en el modelo TCP/IP?
Sesión y Transporte

¿Cuál de los siguientes encapsula la cabecera y el tráiler?
Capa de enlace de datos

¿Qué programa se puede usar para descubrir cortafuegos (firewalls)?
traceroute

¿Cuál de los siguientes ayuda en la identificación (fingerprinting) de una máquina?
Escaneo de puertos

¿Qué tipo de registro DNS proporciona el puerto y los servicios que el servidor está ofreciendo?
SRV

¿Qué valor utiliza un certificado X.509 para identificarlo de forma única?
Número de serie

¿Qué algoritmo de encriptación usa dos números primos grandes factorizados juntos?
RSA

¿Cuál es el valor inicial del SID que se usa para identificar la cuenta de administrador?
500

¿Qué archivo dentro de Linux contiene información administrativa sobre un usuario?
/etc/passwd

¿Qué número de puerto utiliza NetBIOS para los servicios de nombres?
Puerto UDP 137

**¿Qué tipo de regla permite generar registros y alertas en Snort?**
Alert 

¿Qué utilidad muestra las conexiones de red activas en un host?
netstat

En kerberos cuando se solicita un TGT el servidor provee  la server autentication

¿Cuál es un conjunto de extensiones al DNS que proporciona a los clientes DNS (resolvers) autenticación del origen, negación autenticada de existencia e integridad de datos, pero no disponibilidad ni confidencialidad?
**DNSSEC** (Domain Name System Security Extensions) es un conjunto de extensiones del protocolo DNS que añade **seguridad criptográfica** a las respuestas DNS. Específicamente, proporciona:

1. **Autenticación del origen**: el cliente (resolver) puede verificar que la información DNS proviene del servidor legítimo.
    
2. **Negación autenticada de existencia**: permite comprobar de forma segura que un registro **no existe**, usando registros especiales como `NSEC` o `NSEC3`.
    
3. **Integridad de los datos**: garantiza que la información DNS no ha sido modificada durante la transmisión (usando firmas digitales).
    
#### ❗ DNSSEC **no proporciona**:

- **Confidencialidad**: las respuestas DNS siguen siendo públicas (no están cifradas).
    
- **Disponibilidad**: no protege contra ataques de denegación de servicio (DoS) ni garantiza que el servidor esté accesible.

¿Cuál de las siguientes opciones describe mejor un _firewall_ de software?
El _firewall_ de software se coloca entre las aplicaciones normales y los componentes de red del sistema operativo.

NOTA: En el contexto de un curso y examen del EC-Council, piensa en estas definiciones de esta manera: La huella (Footprinting) es una recopilación pasiva de información sin tocar el sistema/red/computadora objetivo.

El escaneo (Scanning) es una recopilación activa de información asociada con un impacto directo en el objetivo.

María realizó un ataque exitoso y obtuvo acceso a un servidor Linux. Ella quiere evitar que un NIDS (Sistema de Detección de Intrusos en la Red) detecte el tráfico saliente desde ese servidor en el futuro.

¿Cuál de las siguientes opciones es la **mejor manera** de evitar la detección por parte del NIDS?
Cifrado (Encryption)
Un **NIDS (Network Intrusion Detection System)** analiza el **tráfico de red sin cifrar**, buscando patrones sospechosos o firmas de ataque en el contenido de los paquetes (payload).  
Si el tráfico está **cifrado**, el NIDS **no puede inspeccionarlo a nivel de contenido**, lo que **oculta comandos, datos o conexiones maliciosas**.

El equipo de desarrollo web está realizando una reunión urgente, ya que han recibido información de los testers sobre una nueva vulnerabilidad en su software web.  
Deciden **modificar los requisitos del software** para **no permitir que los usuarios ingresen HTML como entrada** en su aplicación web.

¿Qué tipo de vulnerabilidad detectó el equipo de pruebas?
### **Cross-site scripting (XSS)**
El hecho de que el equipo haya **decidido bloquear la entrada de HTML del usuario** es una **medida directa contra ataques de XSS (Cross-site scripting)**.

Realizas una investigación y descubres que el **navegador de uno de tus empleados envió solicitudes maliciosas sin que el empleado lo supiera**.  
Identifica la **vulnerabilidad web** que el atacante utilizó en este ataque contra tu empleado.
#### ¿Qué es CSRF?

El **Cross-Site Request Forgery (CSRF)** es un tipo de ataque en el que un **usuario autenticado** es engañado para enviar **peticiones maliciosas sin saberlo**, normalmente al hacer clic en un enlace o cargar una imagen desde un sitio malicioso.

¿Qué tipo de virus intenta ocultarse de los programas antivirus cambiando activamente y corrompiendo las interrupciones de llamadas a servicios del sistema cuando se están ejecutando?
Stealth/Tunneling virus . Un virus de tipo **stealth (sigiloso)** y/o **tunneling (de túnel)** intenta **ocultarse del software antivirus interceptando las llamadas al sistema operativo**, como interrupciones o funciones del sistema.

¿Cuál de los siguientes métodos de prueba de seguridad de aplicaciones corresponde a una **prueba de tipo "caja blanca" (white-box)**, en la que **solo se analiza el código fuente** de las aplicaciones y sus componentes para detectar **posibles vulnerabilidades en el software y la arquitectura**?
Static Application Security Testing es un enfoque de pruebas de seguridad **de caja blanca**

**DAST (Dynamic Application Security Testing)**: Prueba **de caja negra**.

**IAST (Interactive Application Security Testing)**: Combina elementos de SAST y DAST.

**MAST (Mobile Application Security Testing)**: Es un enfoque especializado en la **seguridad de aplicaciones móviles**, y puede usar SAST, DAST, o ambos, pero no es una técnica exclusiva como SAST.

¿Cuál de los siguientes es el **método para determinar el recorrido de un paquete de datos** desde un **host externo no confiable** hacia un **host interno protegido** a través de un **firewall**?
Firewalking

El hacker de sombrero negro Iván quiere implementar un **ataque de hombre en el medio (MITM)** en la red corporativa.  
Para ello, conecta su **propio router** a la red y **redirige el tráfico** para interceptar los paquetes.
¿Qué puede hacer el administrador para **mitigar este ataque**?
Agregar autenticación de mensajes al protocolo de enrutamiento

Bluesnarfing (Robar información a través de Bluetooth)

Bluebugging (tomar el control de un dispositivo a través de Bluetooth) implica obtener acceso remoto a un dispositivo habilitado para Bluetooth y utilizar sus características sin el conocimiento o consentimiento de la víctima

**Bluejacking** es el envío de mensajes no solicitados, de forma anónima, a través de una conexión Bluetooth.

**Bluesmacking**:  
Ataque de denegación de servicio (DoS) que explota una vulnerabilidad en la pila Bluetooth para **bloquear dispositivos** enviando paquetes malformados.

El atacante introduce datos maliciosos en mensajes interceptados dentro de una sesión TCP, ya que el **enrutamiento de origen está deshabilitado**.  
Intenta **adivinar las respuestas** del cliente y del servidor.

¿Qué técnica de secuestro (hijacking) se describe en este ejemplo?
#### **Blind Hijacking**. Es un tipo de **secuestro de sesión TCP/IP** en el que el atacante **no puede ver el tráfico** (no tiene visibilidad directa del intercambio).

**Wireshark** es una de las herramientas más importantes para un especialista en ciberseguridad.  
Se utiliza para el diagnóstico de redes, análisis, desarrollo de software, etc.  
A menudo se trabaja con el panel de **bytes del paquete (packet bytes pane)**.

¿En qué formato se presenta la información en este panel?
**Hexadecimal**

¿Cuál de las siguientes **describe mejor un ataque de inyección de código (code injection)?**
"Forma de ataque en la que un usuario malicioso inserta texto en un campo de datos que es interpretado como código."

Realizas una serie de consultas interactivas, **eligiendo los textos en claro (plaintexts)** siguientes basándote en la **información obtenida de cifrados previos**.

¿Qué tipo de ataque estás intentando realizar?
Adaptive chosen-plaintext attack
ipo avanzado de ataque criptográfico donde:  El atacante **puede elegir textos en claro arbitrarios** para ser cifrados