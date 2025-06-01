Un atacante roba o predice un token de sesión válido para obtener acceso no autorizado a un servidor web o crear una nueva sesión no autorizada. **Usualmente, el secuestro de sesión a nivel de red y a nivel de aplicación ocurren juntos**, ya que un secuestro de sesión a nivel de red exitoso proporciona al atacante suficiente información para llevar a cabo un secuestro de sesión a nivel de aplicación. El secuestro de sesión a nivel de aplicación depende de las sesiones HTTP.

**Techniques**

**▪ Stealing:** El atacante tpuede usar herramientas de "sniffing" como Wireshark o Riverbed Packet Analyzer Plus para interceptar el tráfico entre el cliente y el servidor y extraer los IDs de sesión de los paquetes.

**▪ Guessing:** Un atacante intenta adivinar los IDs de sesión observando las variables de la sesión. En el caso del secuestro de sesión, el rango de valores de ID de sesión que se pueden adivinar es limitado. Por lo tanto, las técnicas de adivinación son efectivas solo cuando los servidores usan mecanismos débiles o defectuosos para la generación de IDs de sesión.

**▪ Brute forcing:** Un atacante obtiene los IDs de sesión intentando todas las permutaciones posibles de valores de IDs de sesión hasta encontrar uno que funcione

A session token can be compromised in various ways:
▪ Session sniffing
▪ Predictable session token
▪ Man-in-the-middle (MITM) attack
▪ Man-in-the-browser attack
▪ Cross-site scripting (XSS) attack
▪ Cross-site request forgery attack
▪ Session replay attack
▪ Session fixation attack
▪ CRIME attack
▪ Forbidden attack
▪ Session donation attack
▪ PetitPotam hijacking

**Compromising Session IDs Using Sniffing** **:** Un atacante utiliza herramientas de "packet sniffing" como Wireshark y Riverbed Packet Analyzer Plus **para interceptar el tráfico HTTP entre una víctima y el servidor web**. Luego analiza los datos en los paquetes capturados para identificar información valiosa, como los IDs de sesión y las contraseñas. Una vez determinado el ID de sesión, el atacante se hace pasar por la víctima y envía el ID de sesión al servidor web antes que la víctima. El atacante utiliza el token de sesión válido para obtener acceso no autorizado al servidor web. De esta manera, el atacante toma control de una sesión legítima existente.

**Compromising Session IDs by Predicting Session Token** **:** Normalmente, los atacantes pueden predecir los IDs de sesión generados por algoritmos débiles e impersonar a un usuario del sitio web.Los atacantes analizan una sección variable de los IDs de sesión para determinar la existencia de un patrón. Este análisis se realiza manualmente o utilizando diversas herramientas criptográficas.Primero, el atacante recopila algunos IDs de sesión válidos que son útiles para identificar usuarios autenticados. Luego, el atacante estudia la estructura del ID de sesión, la información utilizada para generarlo y el algoritmo utilizado por la aplicación web para asegurarla. A partir de estos hallazgos, el atacante puede predecir el ID de sesión.

### ▪ Análisis de patrones de tokens: Tokens secuenciales, Tokens basados en marca de tiempo (timestamp)

**▪ Brute-Force Attacks:** Si el espacio de tokens (el número de posibles tokens) es pequeño, los ataques de fuerza bruta son factibles. Los atacantes intentan todos los tokens posibles hasta encontrar uno válido.

**Compromising Session IDs Using Man-in-the-Middle/Manipulator-in-the-Middle Attack**
Man-in-the-Middle (MITM) o Manipulator-in-the-Middle (MITM) se utiliza para infiltrarse en una conexión existente entre sistemas e interceptar los mensajes que se están transmitiendo. En este ataque, los atacantes emplean diferentes técnicas y dividen una conexión TCP en dos: una conexión cliente-atacante y una conexión atacante-servidor. Después de la interceptación exitosa de una conexión TCP, el atacante puede leer, modificar e insertar datos fraudulentos en la comunicación interceptada. En el caso de una transacción HTTP, la conexión TCP entre el cliente y el servidor es el objetivo.

**Compromising Session IDs Using Man-in-the-Browser/Manipulator-in-the-Browser Attack**

Un ataque Man-in-the-Browser (MITB) o Manipulator-in-the-Browser (MITB) es similar a un ataque MITM, pero la diferencia entre ambos es que un ataque MITB utiliza un caballo de Troya para interceptar y manipular las llamadas entre un navegador y sus mecanismos o bibliotecas de seguridad. Un atacante coloca un caballo de Troya previamente instalado entre el navegador y su mecanismo de seguridad, y el caballo de Troya puede modificar las páginas web y el contenido de las transacciones o insertar transacciones adicionales. Todas las actividades del caballo de Troya son invisibles tanto para el usuario como para la aplicación web.
El objetivo principal de este ataque es el robo financiero mediante la manipulación de transacciones realizadas utilizando sistemas de banca por Internet. Un ataque MITB puede tener éxito incluso en presencia de mecanismos de seguridad como SSL, infraestructura de clave pública (PKI) y autenticación de dos factores, porque todos los controles y mecanismos de seguridad esperados parecerían funcionar normalmente.

**Compromising Session IDs Using Client-side Attacks**

Los ataques del lado del cliente ocurren cuando los clientes establecen conexiones con servidores maliciosos y procesan datos potencialmente dañinos de estos servidores.

**▪ Cross-site scripting (XSS):** permite a los atacantes inyectar scripts maliciosos del lado del cliente en páginas web vistas por otros usuarios.

**▪ Malicious JavaScript codes:** Un atacante puede incrustar en una página web un script malicioso que no genere ninguna advertencia, pero que capture los tokens de sesión en segundo plano y los envíe al atacante.

**▪ Trojans:** Un troyano puede cambiar la configuración del proxy en el navegador del usuario para enviar todas las sesiones a través de la máquina del atacante.

**Compromising Session IDs Using ==Client-side Attacks: Cross-site Script Attack**==

Este tipo de ataque ocurre ==cuando una página web dinámica recibe datos maliciosos del atacante y los ejecuta en el sistema del usuario. los atacantes pueden insertar un JavaScript, VBScript, ActiveX, HTML o un applet Flash malicioso en una página dinámica vulnerable. Esa página luego ejecuta el script en la máquina del usuario y puede recopilar información personal, robar cookies, redirigir a los usuarios a páginas web inesperadas o ejecutar cualquier código malicioso en el sistema del usuario.==

**Flujo del ataque:**
**Paso 1:** El atacante envía un enlace con el script incluido a la víctima. El enlace podría verse algo como esto:
http://victim-site.com/profile?name=\<script\>alert(document.cookie);\</script\>

**Paso 2:** Cuando el usuario visita el enlace, el script malicioso se ejecuta automáticamente, lo que permite al atacante obtener las cookies del usuario, que pueden contener el ID de sesión.

**Paso 3:** El script envía el ID de sesión robado al servidor controlado por el atacante, y ahora puede actuar en nombre de la víctima con esa sesión comprometida.

**Compromising Session IDs Using Client-side Attacks: ==Cross-site Request Forgery Attack(CSRF)**==

==La falsificación de solicitud entre sitios (CSRF), también conocida como ataque de un solo clic, es un ataque en el que el atacante explota la sesión activa de la víctima== con un sitio confiable para realizar actividades maliciosas como compras de artículos y la modificación o recuperación de información de cuentas, el atacante crea un formulario host, que contiene información maliciosa, y lo envía al usuario autorizado. El usuario completa el formulario y lo envía al servidor web. Debido a que los datos provienen de un usuario confiable, el servidor web acepta los datos. ==A diferencia de un ataque XSS, que explota la confianza que un usuario tiene en un sitio web en particular, el CSRF explota la confianza que un sitio web tiene en el navegador de un usuario.==

▪ El atacante aloja una página web con un formulario que parece legítimo. Esta página ya contiene la solicitud del atacante.

▪ Un usuario, creyendo que el formulario es el original, ingresa un nombre de usuario y una contraseña.

▪ Una vez que el usuario completa el formulario, esa página se envía al sitio real.

▪ El servidor del sitio real acepta el formulario, asumiendo que fue enviado por el usuario basado en las credenciales de autenticación. De esta manera, el servidor acepta la solicitud del atacante.

**Compromising Session IDs Using ==Session Replay Attacks**== :
==El atacante captura el token de autenticación de un usuario escuchando una conversación entre el usuario y el servidor. Una vez que el token de autenticación es capturado,  reproduce la solicitud de autenticación al servidor con el token de autenticación capturado para evadir al servidor; como resultado, obtiene acceso no autorizado al servidor.==

**Compromising Session IDs Using ==Session Fixation== :** Un ataque de fijación de sesión es un tipo de secuestro de sesión. Sin embargo, en lugar de robar la sesión establecida entre un usuario y un servidor web después de que el usuario haya iniciado sesión, ==un ataque de fijación de sesión fija una sesión establecida en el navegador del usuario; por lo tanto, el ataque se inicia antes de que el usuario inicie sesión. El atacante usa diversas técnicas para realizar un ataque de fijación de sesión: Token de sesión en el argumento de la URL, Token de sesión en un campo de formulario oculto, ID de sesión en una cookie==
 

==**Session Hijacking Using Proxy Servers**== **:** ==Un atacante induce a la víctima a hacer clic en un enlace falso que parece legítimo, pero que redirige al usuario al servidor del atacante. Luego, el atacante reenvía la solicitud al servidor legítimo en nombre de la víctima y actúa como un intermediario para toda la transacción. Al actuar como un proxy, el atacante captura la información de la sesión durante la interacción entre el servidor legítimo y el usuario.==

**Session Hijacking Using CRIME Attack** :
==Es un ataque del lado del cliente que explota vulnerabilidades en la característica de compresión de datos de protocolos como SSL/Transport Layer Security (TLS), SPDY y HTTP Secure (HTTPS)==. La posibilidad de mitigar la compresión en HTTPS es baja, lo que hace que esta vulnerabilidad sea aún más peligrosa que otras vulnerabilidades de compresión. ==Los atacantes usan herramientas como CrimeCheck para detectar si un servidor web tiene habilitada la compresión TLS o HTTP, y por lo tanto, es vulnerable a ataques CRIME==. Utilizando técnicas de ingeniería social, el atacante engaña a la víctima para que haga clic en un enlace malicioso, capturando el tráfico HTTPS mediante sniffing. Una vez que obtiene la cookie de autenticación, el atacante puede impersonar a la víctima y secuestrar su sesión para robar información confidencial.

**Session Hijacking Using Forbidden Attack** **:** ==Este ataque explota la vulnerabilidad de que la implementación de TLS reutiliza incorrectamente el mismo "nonce" (un número único usado una vez)cuando los datos se cifran utilizando el modo de cifrado avanzado Galois/Counter (AES-GCM) durante el apretón de manos TLS. Explotan esta vulnerabilidad para realizar un ataque MITM generando claves criptográficas usadas para la autenticación.== Al repetir el mismo nonce durante el apretón de manos TLS, un atacante puede monitorear y secuestrar la conexión.

**Session Hijacking Using Session Donation Attack** **:** ==El atacante dona su propia sesión válida al usuario objetivo. El atacante primero obtiene una ID de sesión válida al iniciar sesión en un servicio y luego envía esa misma ID de sesión al usuario objetivo. Cuando el usuario hace clic en el enlace y ingresa sus detalles (nombre de usuario, contraseña, datos de pago, etc.), esos datos se vinculan a la cuenta del atacante sin que la víctima lo sepa.== El atacante puede llevar a cabo este ataque utilizando técnicas como cookies entre sitios, ataques MITM (man-in-the-middle) y fijación de sesión.