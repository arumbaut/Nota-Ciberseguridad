**Analyzing Android Devices**

**Source:** **https://mas.owasp.org**

Analizar dispositivos Android implica examinar el sistema para recopilar información, entender su comportamiento o identificar vulnerabilidades para diversos propósitos.  
Un atacante puede analizar el dispositivo Android objetivo conectándolo a su estación de trabajo y creando acceso a la terminal utilizando la herramienta de línea de comandos **ADB**.

**▪ List Out the Open Connections**
Attackers can run the following netstat command on the connected Android device to obtain information about the network activity by specifying the process ID:

 **# netstat -p | grep \<pid\>**

**▪ Monitoring Logs**

$ adb logcat > logcat.log

**▪ Disassemble the Targeted App Package**

$ apktool d <App_package>.apk $ tree

Other Techniques for Hacking Android Devices

**▪ Advanced SMS Phishing**

El atacante puede llevar a cabo este ataque utilizando cualquier módem USB de bajo costo y engañando al usuario para que acepte los nuevos ajustes, es decir, ajustes maliciosos, en el dispositivo móvil, los cuales pueden redirigir los datos del usuario al atacante. El vector de ataque depende principalmente de un proceso llamado provisionamiento Over-the-Air (OTA), que es utilizado principalmente por los operadores de red.

**Android Malware**

**▪ Mamont Source: https://www.gdatasoftware.com**

Mamont es un troyano bancario para Android que se disfraza de aplicación del navegador Chrome, con el objetivo de engañar a los usuarios para que descarguen e instalen el troyano sin darse cuenta. Este tipo de malware generalmente se distribuye a través de correos electrónicos de phishing y mensajes de spam. Al instalarse, el troyano se activa y solicita al usuario que conceda permisos específicos, incluyendo la capacidad de iniciar y supervisar llamadas telefónicas, así como enviar y recibir SMS.

**Android Hacking Tools**

==**▪ AndroRAT== 
Source: https://github.com**

AndroRAT is a tool designed to provide remote control to an Android system and retrieve information from it

==Ghost Framework==
Source: https://github.com**

is an Android post-exploitation tool that leverages the Android debugging bridge (ADB) to gain remote access to Android devices

Some additional Android hacking tools are as follows:
▪ hxp_photo_eye (https://github.com)
▪ Gallery Eye (https://github.com)
▪ mSpy (https://www.mspy.com)
▪ Hackingtoolkit (https://github.com)
▪ Social-Engineer Toolkit (SET) (https://github.com)

**Android-based Sniffers**

**▪ PCAPdroid Source: https://play.google.com**
Permite a los atacantes rastrear, examinar y bloquear conexiones realizadas por otras aplicaciones, simulando una VPN para capturar el tráfico de red sin necesidad de acceso root. También permite a los atacantes monitorear y analizar el tráfico de red en dispositivos Android. Además, esta aplicación puede procesar todos los datos localmente en el dispositivo sin utilizar un servidor remoto.

**Some additional Android-based sniffers are as follows:**
▪ NetCapture (https://play.google.com)
▪ Intercepter-NG (http://sniff.su)
▪ Packet Capture (https://play.google.com)
▪ Sniffer Wicap 2 Demo (https://www.9apps.com)
▪ Reqable API Testing & Capture (https://play.google.com)
  
**Securing Android Devices**
▪ Habilita el bloqueo de pantalla para tu teléfono Android  
▪ Usa contraseñas fuertes y biometría:  
o Establece una contraseña, PIN o patrón de bloqueo fuerte  
o Habilita la autenticación biométrica como huella digital o reconocimiento facial  
▪ Nunca rootear tu dispositivo Android  
▪ Descarga aplicaciones solo desde mercados oficiales de Android  
▪ Mantén tu dispositivo actualizado con software antivirus para Android como Kaspersky Antivirus  
▪ No descargues APKs directamente  
▪ Actualiza el sistema operativo regularmente

**Android Security Tools**
▪ Kaspersky Antivirus for Android Source: https://www.kaspersky.com
▪ Avira Security Antivirus & VPN (https://play.google.com)
▪ Avast Antivirus & Security (https://play.google.com)
▪ McAfee Security: Antivirus VPN (https://play.google.com)
▪ Lookout Mobile Security and Antivirus (https://play.google.com)
▪ Sophos Intercept X for Mobile (https://play.google.com)
  
**Android Device Tracking Tools**
▪ Google Find My Device Source: https://www.google.com
▪ Find My Phone Source: https://play.google.com
▪ Where’s My Droid Source: https://wheresmydroid.com

**Some additional Android device tracking tools are as follows:**

▪ Prey: Find My Phone & Security (https://play.google.com)
▪ Phone Tracker and GPS Location (https://play.google.com)
▪ Mobile Tracker for Android (https://play.google.com)
▪ Lost Phone Tracker (https://play.google.com)
▪ Phone Tracker By Number (https://play.google.com)
 
**Android Vulnerability Scanners**
▪ Quixxi App Shield Source: https://quixxi.com Quixxi
App Shield can be used by enterprises and mobile app developers to secure their mobile apps from piracy, revenue loss, intellectual property (IP) theft, loss of user data.

**Some additional Android vulnerability scanners are as follows:**
▪ Android Exploits (https://play.google.com)
▪ ImmuniWeb® MobileSuite (https://www.immuniweb.com)
▪ Yaazhini (https://www.vegabird.com)
▪ Vulners Scanner (https://play.google.com)

**Análisis Estático de APK de Android**Los analistas de seguridad realizan un análisis estático de los APKs maliciosos de Android para examinar el código sin ejecutar la aplicación. Este método ayuda a identificar características perjudiciales en las aplicaciones, como la exfiltración de datos, espionaje o modificaciones no autorizadas del sistema. También revela vulnerabilidades como codificación débil, contraseñas embebidas y bibliotecas desactualizadas que pueden ser explotadas por atacantes.

**Análisis Estático de APK de Android Usando el Mobile Security Framework (MobSF)**Los analistas de seguridad pueden usar la herramienta Mobile Security Framework (MobSF) para realizar análisis estáticos y dinámicos de archivos APK de Android sospechosos.

▪ MobSF Source:
https://github.com MobSF
Is a multipurpose tool that automates malware analysis and security assessment using static and dynamic analysis abilities.

**Online Android Analyzers**
▪ Sixo Online APK Analyzer Source: https://sisik.eu

**Some additional online Android analyzers are as follows:**
▪ ShenmeApp (https://www.shenmeapp.com)
▪ KOODOUS (https://koodous.com)
▪ Android Apk decompiler (http://www.javadecompilers.com)
▪ Hybrid Analysis (https://www.hybrid-analysis.com)
▪ DeGuard (http://apk-deguard.com)