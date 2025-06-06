**Mobile Spam**

El spam móvil, también conocido como spam por SMS, spam de texto o m-spam, hace referencia a los mensajes no deseados enviados de forma masiva a números de teléfono o direcciones de correo electrónico conocidas o desconocidas con el objetivo de llegar a dispositivos móviles.

**Los tipos más comunes de mensajes spam enviados a teléfonos móviles incluyen:**▪ Mensajes con anuncios o enlaces maliciosos diseñados para engañar al usuario y hacer que revele información confidencial.  
▪ Mensajes comerciales atractivos que promocionan productos o servicios.  
▪ Mensajes SMS o MMS que afirman que la víctima ha ganado un premio y la instan a llamar a un número de teléfono de tarifa premium para obtener más información.  
▪ Enlaces maliciosos diseñados para atraer a los usuarios y hacer que revelen datos personales o corporativos sensibles.  
▪ Mensajes de phishing que intentan engañar al destinatario para que proporcione datos personales o financieros, como nombre, dirección, fecha de nacimiento, número de cuenta bancaria, número de tarjeta de crédito, entre otros, que un atacante podría utilizar para cometer fraudes financieros o de identidad.

**SMS Phishing Attack (SMiShing) (Targeted Attack Scan)**

El phishing por SMS, también conocido como SMiShing, es un tipo de fraude de phishing en el que un atacante utiliza sistemas de mensajería SMS para enviar mensajes falsos. Se trata del intento de obtener información personal y financiera mediante el envío de SMS (o mensajes de mensajería instantánea) que contienen enlaces engañosos.

Estos mensajes fraudulentos suelen incluir una URL falsa o un número de teléfono, con el fin de engañar a las víctimas y hacer que revelen datos personales o financieros, como números de seguro social, tarjetas de crédito, y credenciales de banca en línea. Además, los atacantes pueden utilizar SMiShing para infectar los teléfonos móviles de las víctimas, así como las redes asociadas, con malware.

**Pairing Mobile Devices on Open Bluetooth and Wi-Fi Connections**

**▪ Bluesnarfing (Stealing information via Bluetooth)**

El bluesnarfing es el robo de información desde un dispositivo inalámbrico mediante una conexión Bluetooth, generalmente entre teléfonos, computadoras de escritorio, portátiles, PDAs y otros dispositivos. Esta técnica permite que un atacante acceda a la lista de contactos de la víctima, correos electrónicos, mensajes de texto, fotos, videos y datos empresariales almacenados en el dispositivo.

Cualquier dispositivo con la conexión Bluetooth activada y configurado como "visible" (permitiendo que otros dispositivos Bluetooth dentro del alcance lo detecten) puede ser vulnerable al bluesnarfing si el software del proveedor presenta alguna vulnerabilidad específica.  
El bluesnarfing se aprovecha de las conexiones Bluetooth de otros sin su conocimiento.

**▪ Bluebugging (Taking over a device via Bluetooth)**

El bluebugging consiste en obtener acceso remoto a un dispositivo con Bluetooth activado y utilizar sus funciones sin el conocimiento ni el consentimiento del propietario. Los atacantes comprometen la seguridad del dispositivo objetivo mediante un ataque de tipo backdoor (puerta trasera) antes de devolver el control al usuario legítimo.

El bluebugging permite a los atacantes espiar datos personales o corporativos sensibles, recibir llamadas y mensajes destinados a la víctima, interceptar llamadas y mensajes, reenviar comunicaciones, conectarse a Internet, y realizar otras actividades maliciosas, como acceder a listas de contactos, fotos y videos.

**Agent Smith Attack**

Los ataques Agent Smith se ejecutan engañando a las víctimas para que descarguen e instalen aplicaciones maliciosas, publicadas por los atacantes en forma de juegos, editores de fotos u otras herramientas atractivas, a través de tiendas de aplicaciones de terceros, como 9Apps.Una vez que el usuario instala la aplicación, el código malicioso oculto dentro de ella infecta o reemplaza aplicaciones legítimas en el dispositivo móvil de la víctima, mediante comandos de control y comando (C&C). La aplicación engañosa sustituye apps legítimas como WhatsApp, SHAREit o MX Player por versiones infectadas que conservan la apariencia funcional original.

**Exploiting SS7 Vulnerability**

El Signaling System 7 (SS7) es un protocolo de comunicación que permite a los usuarios móviles intercambiar comunicaciones a través de otras redes celulares, especialmente durante el roaming (itinerancia).Este mecanismo de señalización opera sobre la base de la confianza mutua entre los operadores, sin requerir autenticación ni verificación de identidad. Dado que la red de señalización SS7 no está aislada, los atacantes pueden explotar esta vulnerabilidad para ejecutar ataques de tipo Man-in-the-Middle (MITM), interceptando mensajes de texto y llamadas entre los dispositivos que se comunican.A través de esta técnica, el atacante puede escuchar credenciales bancarias, contraseñas de un solo uso (OTP) y otra información sensible que se transmite por la red. Esta vulnerabilidad en SS7 también puede permitir al atacante eludir la autenticación de dos factores (2FA) e incluso comprometer la cifrado de extremo a extremo basado en SMS.

**Simjacker: Ataque a través de la Tarjeta SIM**Simjacker es una vulnerabilidad asociada al navegador S@T (SIMalliance Toolbox Browser) de la tarjeta SIM, un software preinstalado en muchas tarjetas SIM que permite ejecutar un conjunto de instrucciones específicas.

Los atacantes explotan esta vulnerabilidad del navegador S@T para llevar a cabo diversas actividades maliciosas

**Call Spoofing** 

La suplantación de llamadas es una técnica utilizada por los atacantes para manipular la información del identificador de llamadas (caller ID) que se muestra en el teléfono del destinatario cuando recibe una llamada. Los atacantes emplean esta técnica para disfrazar su número de teléfono como si fuera una fuente confiable, como un banco o una agencia gubernamental, con el fin de engañar a las personas para que compartan información sensible o paguen por servicios innecesarios

**T****ools that an attacker can use to perform call spoofing**

**▪ SpoofCard Source: https://www.spoofcard.com**
▪ Fake Call (https://play.google.com)
▪ SpoofTel (https://www.spooftel.com)
▪ Fake Call and SMS (https://play.google.com)
▪ Fake Caller ID (https://fakecallerid.io)
▪ Phone Id - Fake Caller Buster (https://play.google.com)

**OTP Hijacking/Two-Factor Authentication Hijacking**
Las contraseñas de un solo uso (OTPs) son enviadas por un servidor mediante SMS, una aplicación de autenticación o correo electrónico para la autenticación segura de los usuarios. Aunque esta característica parece segura, los atacantes pueden secuestrar los OTPs y redirigirlos a sus propios dispositivos utilizando diversas técnicas como la ingeniería social y el SMS jacking.Este ataque es difícil de detectar, ya que los usuarios podrían sospechar que hay un problema de red cuando no reciben un OTP, cuando en realidad el OTP ha sido redirigido a un dispositivo controlado por el atacante.Los atacantes también pueden usar ataques de SIM jacking para infectar la SIM del dispositivo objetivo mediante malware, lo que les permite interceptar y leer los OTPs.

**OTP Hijacking via Lock Screen Notifications**

Los atacantes roban físicamente los OTP basados en SMS del teléfono móvil del usuario objetivo al monitorear de cerca las acciones del usuario. Pueden ver las notificaciones en la pantalla de bloqueo del dispositivo cuando el usuario solicita un OTP. Los atacantes pueden secuestrar las notificaciones de la pantalla de bloqueo utilizando diferentes métodos, tales como escuchar en secreto o engañar al usuario para que preste su teléfono con el pretexto de hacer una llamada de emergencia.

**OTP Hijacking Tools**

**▪ AdvPhishing Source: https://github.com**

AdvPhishing is a social media phishing tool that assists attackers in bypassing two-factor or OTP authentication

**▪ mrphish Source: https://github.com**

mrphish is a bash-based script used for phishing social media accounts with port forwarding and OTP bypassing control. This tool works on both rooted and non-rooted Android devices.

**Camfecting Attack**

Un ataque camfecting es un ataque de captura de cámara web. En este ataque, el atacante obtiene acceso a la cámara de la computadora o dispositivo móvil de la víctima. El atacante infecta el dispositivo objetivo con un troyano de acceso remoto (RAT) y lo compromete para acceder a la cámara y el micrófono de la víctima. Además, el atacante puede desactivar la luz de la cámara para evitar ser detectado.

**Android Camera Hijack Attack**

Un atacante puede explotar las múltiples vulnerabilidades de bypass de seguridad de Android para eludir los permisos requeridos y obtener acceso a la cámara y el micrófono de la víctima. Además, el atacante puede explotar esta vulnerabilidad incluso si el dispositivo móvil está bloqueado.Las aplicaciones de cámara en Android generalmente requieren permisos de almacenamiento para guardar fotos y videos.

**Camera/Microphone Hijacking**

**Tools**
▪ StormBreaker Source: https://www.github.com

**The following are some additional camera/microphone hacking tools:**

▪ CamPhish (https://www.github.com)
▪ HACK-CAMERA (https://www.github.com)
▪ E-TOOL (https://github.com) ▪ CamOver (http://www.github.com)
▪ CAM-DUMPER (https://github.com)

**Android Rooting**

**El objetivo del rooteo en Android** es superar las restricciones impuestas por los fabricantes de hardware y las operadoras, lo que permite modificar o reemplazar aplicaciones y configuraciones del sistema, ejecutar aplicaciones que requieren privilegios de administrador, eliminar y reemplazar el sistema operativo del dispositivo, eliminar aplicaciones preinstaladas por el fabricante o la operadora, o realizar otras operaciones que normalmente no están disponibles para un usuario típico de Android.

Con el acceso root, las aplicaciones instaladas por el usuario pueden ejecutar comandos privilegiados como:

▪ Modificar o eliminar archivos del sistema, módulos, ROMs (firmware original) y kernels  
▪ Eliminar aplicaciones instaladas por el fabricante o la operadora (bloatware)  
▪ Acceder a bajo nivel al hardware, algo que no es posible en la configuración predeterminada del dispositivo  
▪ Mejorar el rendimiento del dispositivo  
▪ Compartir Internet mediante Wi-Fi o Bluetooth (tethering)  
▪ Instalar aplicaciones directamente en la tarjeta SD  
▪ Personalizar la interfaz de usuario y el teclado

Sin embargo, el rooteo conlleva **diversos riesgos de seguridad y posibles problemas**, tales como:

▪ Anulación de la garantía del dispositivo  
▪ Bajo rendimiento  
▪ Infección por malware  
▪ “Brickeo” del dispositivo (daños que lo hacen inoperable)

**Rooting Android Using KingoRoot**
Source: https://www.kingoapp.com
KingoRoot is a tool used to root Android devices. It can be used with or without a PC. KingoRoot helps users root their Android devices to achieve the following:

▪ Preserve battery life
▪ Access root-only apps
▪ Remove carrier “bloatware”
▪ Customize appearance
▪ Attain admin level permission

**Android Rooting Tools**
▪ One Click Root Source: https://oneclickroot.com
▪ TunesGo (https://tunesgo.wondershare.com)
▪ RootMaster (https://root-master.com)
▪ Magisk Manager (https://magiskmanager.com)
▪ KingRoot (https://kingrootapp.net)
▪ iRoot (https://iroot-download.com)

Bypassing FRP on Android Phones Using 4ukey
Source: https://www.tenorshare.net
**Los atacantes pueden eludir la FRP** explotando vulnerabilidades de software o utilizando herramientas especializadas como **4uKey** y **Octoplus FRP**
Una vez que el atacante logra evadir esta protección, puede obtener acceso a datos personales almacenados en el dispositivo.

**Hacking with zANTI and Kali NetHunter**

▪ Hacking Networks Using zANTI Source: https://www.zimperium.com
zANTI is an Android application that allows you to perform the following attacks:

**Spoof MAC Address**
Create malicious Wi-Fi hotspot to capture victims to control and hijack their device traffic

**Scan for open ports**
Exploit router vulnerabilities
Password complexity audits
MITM and DoS attack
View, modify, and redirect all HTTP requests and responses
Redirect HTTPS to HTTP; redirect HTTP request to a particular IP or web page
Insert HTML code into web pages
Hijack sessions
View and replace all images that are transmitted over the network
Capture and intercept downloads
  
▪ Hacking Networks Using Kali NetHunter
Source: https://www.kali.org
### **Kali NetHunter**

Kali NetHunter proporciona un conjunto completo de herramientas que permite a los atacantes llevar a cabo diversos tipos de ataques, tales como:

² Ataques HID (Human Interface Device) mediante emulación de teclado
² Ataques BadUSB
² Ataques maliciosos de punto de acceso (evil AP) con MANA sobre dispositivos Android

Además, esta herramienta permite a los atacantes generar cargas útiles personalizadas usando Metasploit para comprometer redes objetivo.

² El atacante simplemente debe:
² Seleccionar la carga útil deseada
² Configurar las opciones correspondientes
² Generar una payload adecuada para la intrusión
### Lanzar ataque DoS utilizando Low Orbit Ion Cannon (LOIC)

### LOIC es una aplicación móvil que permite a los atacantes realizar ataques DoS/DDoS sobre una dirección IP objetivo.

Esta aplicación puede llevar a cabo ataques de inundación UDP, HTTP o TCP.
Hacking with Orbot Proxy
Source: https://orbot.app
Orbot es una aplicación proxy que permite a otras aplicaciones usar Internet de manera más privada.Utiliza Tor para cifrar tu tráfico de Internet y luego lo oculta redirigiéndolo a través de una serie de computadoras alrededor del mundo.  
Los atacantes pueden usar esta aplicación para ocultar su identidad mientras realizan ataques o navegan por aplicaciones web objetivo.

Exploiting Android Device through ADB Using PhoneSploit Pro
Source: https://github.com
Android Debug Bridge (ADB) is a command-line tool that allows attackers to communicate with the target Android device. This tool provides various features to install and debug apps and access the Unix shell to execute various shell commands on a device.

**Launching Spearphone Attack**Un ataque Spearphone permite a las aplicaciones Android grabar datos del altavoz sin requerir privilegios especiales.  
Los atacantes pueden espiar conversaciones de voz del altavoz entre usuarios móviles remotos explotando el sensor de movimiento basado en hardware, es decir, el acelerómetro.El sensor de movimiento permite a las aplicaciones capturar el movimiento físico del dispositivo en función de los cambios en la posición y la velocidad.  
Las reverberaciones del habla también pueden ser grabadas a través de este sensor incorporado, ya que el altavoz se encuentra en la misma superficie del dispositivo.