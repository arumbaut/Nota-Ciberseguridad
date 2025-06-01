**DNS Server Hijacking:** 
Un atacante compromete un servidor DNS y cambia su configuración de mapeo para redirigir hacia un servidor DNS falso que redirigirá las solicitudes del usuario al servidor falso del atacante.

**DNS Amplification Attack :**
Es un tipo de ataque de **reflejo y amplificación** en el que un atacante utiliza servidores DNS abiertos para enviar grandes cantidades de datos al sistema víctima. ==La clave del ataque está en **enviar pequeñas solicitudes y hacer que los servidores DNS respondan con respuestas mucho más grandes**, redirigidas al objetivo.==

**Directory Traversal Attacks :**
==Es la explotación de HTTP mediante la cual los atacantes pueden acceder a directorios restringidos y ejecutar comandos fuera del directorio raíz del servidor web manipulando una URL== (Localizador Uniforme de Recursos). En los ataques de traversal de directorio, los atacantes utilizan la secuencia de puntos (../) para acceder a directorios restringidos fuera del directorio raíz del servidor web.

**Website Defacement****:**
==Los atacantes utilizan una variedad de métodos, como la inyección de MySQL, para acceder a un sitio web y desfigurarlo. Además de cambiar la apariencia visual del sitio web objetivo, los atacantes desfiguran sitios web para infectar las computadoras de los visitantes, haciendo que el sitio sea vulnerable a ataques de virus.==

**Web Server Misconfiguration****:
**▪ Mensajes de depuración/error verbosos,
▪ Usuarios/contraseñas anónimos o predeterminados, 
▪ Archivos de configuración y scripts de muestra,
▪ Funciones de administración remota.

**HTTP Response-Splitting Attack:** 
==El atacante engaña al servidor inyectando nuevas líneas en los encabezados de respuesta, junto con código arbitrario. Implica agregar datos de encabezado de respuesta en el campo de entrada para que el servidor divida la respuesta en dos respuestas==. Este tipo de ataque explota vulnerabilidades en la validación de entrada. Cross-site scripting (XSS), falsificación de solicitudes entre sitios (CSRF) y la inyección de lenguaje de consulta estructurado (SQL) son ejemplos de este tipo de ataque.

**Web Cache Poisoning Attack:** 
En este ataque, ==un atacante intercambia contenido en caché para una URL aleatoria con contenido infectado.== Los usuarios de la fuente de caché web pueden usar sin saberlo el contenido envenenado en lugar del contenido verdadero y seguro

**SSH Brute Force Attack:**
==Con la ayuda de un ataque de fuerza bruta, el atacante obtiene credenciales de inicio de sesión para obtener acceso no autorizado a un túnel SSH. Un atacante que obtiene las credenciales de inicio de sesión de SSH puede usar los mismos túneles SSH para transmitir malware y otros medios de explotación a las víctimas sin ser detectado.==

**FTP Brute Force with AI:**
Los atacantes pueden aprovechar tecnologías impulsadas por inteligencia artificial (IA) para mejorar y automatizar los intentos de fuerza bruta.

Ejemplo

An attacker can use ChatGPT to perform this task by using an appropriate prompt such as

“Attempt FTP login on target IP 10.10.1.11 with hydra using usernames and passwords from wordlists”

The output of this prompt results in the following command:

hydra -L /usr/share/wordlists/ftp-usernames.txt -p /usr/share/wordlists/ftp-passwords.txt ftp://10.10.1.11

**HTTP/2 Continuation Flood Attack:**
==Los atacantes explotan este mecanismo enviando numerosos marcos CONTINUATION a través de una sola conexión TCP sin completar los encabezados, lo que sobrecarga los recursos del servidor Apache y causa una condición de denegación de servicio (DoS) en el servidor.==

**Frontjacking Attack:** 
==El frontjacking es un tipo de ataque a servidores web en el que un atacante inyecta o manipula los componentes del front-end de una aplicación web, como scripts o elementos HTML, para secuestrar la interfaz de usuario o las interacciones del usuario. A menudo se dirige a servidores proxy inversos Nginx mal configurados.

**Web Server Password Cracking:**

**Techniques :** 
**▪ Guessing :**
Este es el método más común para descifrar contraseñas. En este método, el atacante adivina posibles contraseñas ya sea manualmente o utilizando herramientas automatizadas que vienen con diccionarios.
**▪ Dictionary attack:** 
Un ataque de diccionario utiliza un archivo predefinido que contiene diversas combinaciones de palabras, y un programa automatizado ingresa estas palabras una por una para verificar si alguna de ellas es la contraseña. Esto podría no ser efectivo si la contraseña incluye caracteres especiales y símbolos. Si la contraseña es una palabra simple, entonces puede encontrarse rápidamente.
**▪ Brute-force attack**: 
En el método de fuerza bruta, se prueban todas las combinaciones posibles de caracteres; por ejemplo, la prueba puede incluir combinaciones de letras mayúsculas de la A a la Z, números del 0 al 9 y letras minúsculas de la a a la z. Este método es útil para identificar contraseñas de una o dos palabras. Si una contraseña contiene letras mayúsculas, minúsculas y caracteres especiales, podría tomar meses o incluso años descifrarla mediante un ataque de fuerza bruta.
**▪ Hybrid attack:**
Es más poderoso que las técnicas anteriores porque utiliza tanto un ataque de diccionario como un ataque de fuerza bruta. También emplea símbolos y números. El descifrado de contraseñas es más fácil con este método que con los anteriores.

**DoS/DDoS Attacks:** 
implica inundar a los objetivos con numerosas solicitudes falsas para que el objetivo deje de funcionar y se vuelva inaccesible para los usuarios legítimos. Mediante un ataque DoS/DDoS a un servidor web, un atacante intenta derribar el servidor web o hacerlo inaccesible para los usuarios legítimos.

**Man-in-the-Middle Attack**:
Permiten a un atacante acceder a información sensible interceptando y alterando las comunicaciones entre un usuario final y los servidores web. En un ataque MITM, también conocido como ataque de sniffing, un intruso intercepta o modifica los mensajes intercambiados entre el usuario y el servidor web mediante la escucha no autorizada o la intrusión en la conexión

**Phishing Attacks**
Los atacantes llevan a cabo un ataque de _phishing_ enviando un correo electrónico que contiene un enlace malicioso y engañando al usuario para que haga clic en él. Al hacer clic, el usuario es redirigido a un sitio web falso que aparenta ser el sitio legítimo. Los atacantes crean estos sitios web falsos alojando su dirección en servidores web propios. Cuando la víctima hace clic en el enlace malicioso creyendo que se trata de la dirección de un sitio web legítimo, es redirigida al sitio malicioso alojado en el servidor del atacante

