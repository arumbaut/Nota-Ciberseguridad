
#### **Service Hijacking using Social Engineering** 

==En el secuestro de cuentas o servicios, un atacante roba las credenciales de un CSP o de un cliente mediante phishing, pharming, ingeniería social y explotación de vulnerabilidades de software. Con las credenciales robadas, el atacante obtiene acceso a los servicios de computación en la nube y compromete la confidencialidad, integridad y disponibilidad de los datos.==
Los atacantes pueden dirigirse a los [^1]CSP para restablecer contraseñas o al personal de TI para acceder a sus servicios en la nube y revelar contraseñas. Otras formas de obtener contraseñas incluyen la adivinación de contraseñas, el malware keylogging, la implementación de técnicas de descifrado de contraseñas y el envío de correos electrónicos de phishing. Los ataques de ingeniería social dan como resultado la exposición de datos de clientes y tarjetas de crédito, información personal, planes de negocios, datos del personal, robo de identidad, etc.

#### **Service Hijacking using Network Sniffing** 

Secuestro de servicios mediante rastreo de red. El rastreo de red implica la interceptación y monitorización del tráfico de red entre dos nodos de la nube. Los datos confidenciales sin cifrar (p. ej., credenciales de inicio de sesión) durante la transmisión a través de una red corren un alto riesgo. Los atacantes utilizan rastreadores de paquetes (p. ej., Wireshark) para capturar datos confidenciales, como contraseñas y cookies de sesión, y otros datos de configuración de seguridad relacionados con servicios web, como el protocolo universal de descubrimiento e integridad de descripciones ([^2]UDDI), el protocolo simple de acceso a objetos ([^3]SOAP) y los archivos de lenguaje de descripción de servicios web ([^4]WSDL).

#### **Side-Channel Attacks or Cross-guest VM Breaches** 

Ataques de canal lateral o vulneraciones de máquinas virtuales entre huéspedes. ==Los atacantes pueden comprometer la nube colocando una máquina virtual maliciosa cerca de un servidor en la nube objetivo y luego lanzando un ataque de canal lateral==.  El atacante ejecuta la máquina virtual en el mismo host físico que la máquina virtual objetivo y aprovecha los recursos físicos compartidos (caché del procesador). Luego, lanza ataques de canal lateral (ataque de temporización, remanencia de datos, criptoanálisis acústico, ataque de monitorización de energía y análisis de fallos diferenciales) para extraer claves criptográficas/secretos de texto plano y robar las credenciales de la víctima. Los ataques de canal lateral pueden ser implementados por cualquier usuario residente y se relacionan principalmente con vulnerabilidades en recursos tecnológicos compartidos. Finalmente, el atacante utiliza las credenciales robadas para suplantar la identidad de la víctima.

#### **Wrapping Attack** 

 ==Un ataque de envoltorio se realiza durante la traducción del mensaje SOAP en la capa TLS. Los atacantes duplican el cuerpo del mensaje y lo envían al servidor como si fuera un usuario legítimo.== Cuando los usuarios envían una solicitud desde su máquina virtual a través de un navegador, esta llega primero al servidor web. A continuación, se genera un mensaje SOAP con información estructural que se intercambia con el navegador durante el envío del mensaje. Antes de que se produzca el envío del mensaje, el navegador debe firmar el documento XML y canonizarlo. Además, debe añadir los valores de la firma al documento. Finalmente, el encabezado SOAP debe contener la información necesaria para el destino después del cálculo. ==En un ataque de envoltorio, el engaño al adversario se produce durante la traducción del mensaje SOAP en la capa TLS. El atacante duplica el cuerpo del mensaje y lo envía al servidor como si fuera un usuario legítimo. El servidor comprueba la autenticación mediante el valor de la firma (que también está duplicado) y verifica su integridad. Como resultado, el adversario puede invadir la nube y ejecutar código malicioso para interrumpir el funcionamiento normal de los servidores en la nube.==

#### **Man-in-the-Cloud (MITC) Attack** 

==Los ataques MITC son una versión avanzada de los ataques MITM. En estos ataques, el atacante utiliza un exploit que intercepta y manipula la comunicación entre dos partes, mientras que los ataques MITC se llevan a cabo abusando de servicios de sincronización de archivos en la nube, como Google Drive o DropBox, para la vulneración de datos, el comando y control (C&C), la exfiltración de datos y el acceso remoto==. Los tokens de sincronización se utilizan para la autenticación de aplicaciones en la nube, pero no pueden distinguir el tráfico malicioso del tráfico normal. Los atacantes aprovechan esta vulnerabilidad en las cuentas en la nube para realizar ataques MITC.

#### **Cloud Hopper Attack** 

==Ataque de salto de nube. Los ataques de salto de nube se desencadenan contra proveedores de servicios gestionados ([^5]MSP) y sus clientes. Una vez implementado con éxito, los atacantes pueden obtener acceso remoto a la propiedad intelectual e información crítica del MSP objetivo y sus usuarios/clientes globales. Los atacantes también se mueven lateralmente en la red, de un sistema a otro en el entorno de nube, para obtener mayor acceso a datos confidenciales de entidades industriales, como manufactura, organismos gubernamentales, atención médica y finanzas.== Los atacantes inician correos electrónicos de phishing selectivo con malware personalizado para comprometer las cuentas de usuario de empleados o empresas de servicios en la nube y obtener información confidencial. Los atacantes también pueden usar scripts basados ​​en comandos de PowerShell y PowerSploit para reconocimiento y recopilación de información. Los atacantes utilizan la información recopilada para acceder a otros sistemas conectados a la misma red. Para llevar a cabo este ataque, los atacantes también utilizan el C&C de sitios que suplantan dominios legítimos y malware sin archivos que reside y se ejecuta desde la memoria. 

#### **Cloud Cryptojacking** 

==El criptojacking consiste en el uso no autorizado del ordenador de la víctima para extraer criptomonedas de forma sigilosa. Los ataques de criptojacking son muy lucrativos e involucran tanto a atacantes externos como a infiltrados internos. Para llevar a cabo este ataque, los atacantes aprovechan vectores de ataque como configuraciones incorrectas en la nube, sitios web comprometidos y vulnerabilidades del lado del cliente o del servidor==. Por ejemplo, un atacante explota instancias de la nube mal configuradas para inyectar una carga útil maliciosa de criptominería en una página web o una biblioteca de terceros cargada por la página web. Luego, el atacante induce a la víctima a visitar la página web maliciosa y, cuando la abre, se ejecuta automáticamente el criptominero en su navegador mediante JavaScript. Mediante criptomineros basados ​​en JavaScript, como CoinHive y Cryptoloot, los atacantes pueden incrustar fácilmente scripts maliciosos de criptominería en sitios web legítimos mediante un enlace a CoinHive. Los atacantes complican este ataque ocultando el script malicioso de criptominería mediante diversas técnicas de ocultación, como codificación, redirecciones y ofuscación. La configuración de la carga útil suele ser dinámica o estar codificada. Los ataques de cryptojacking pueden causar graves impactos en sitios web, endpoints e incluso en toda la infraestructura de la nube.

#### **Cloudborne Attack**

Ataque Cloudborne. Cloudborne es una vulnerabilidad que reside en un servidor en la nube físico que permite a los atacantes implantar una puerta trasera maliciosa en su firmware. La puerta trasera instalada puede persistir incluso si el servidor se reasigna a nuevos clientes o empresas que lo utilizan como IaaS. Los servidores físicos no están confinados a un solo cliente y pueden transferirse de un cliente a otro. Durante el proceso de recuperación, si la actualización del firmware (configuración predeterminada de fábrica, borrado completo de la memoria, etc.) no se implementa correctamente, las puertas traseras pueden permanecer activas en el firmware y propagarse por el servidor.

#### **Instance Metadata Service (IMDS) Attack** 

Un servicio de metadatos de instancia (IMDS) proporciona información sobre una instancia, su red asociada y el software configurado para ejecutarla. IMDS también genera credenciales para los roles asociados a una instancia. Según el rol o la política asignados, el software configurado en la instancia también puede acceder a los recursos del almacenamiento en la nube. ==Los atacantes realizan ataques IMDS explotando una vulnerabilidad de día cero en el servidor de aplicaciones objetivo o utilizando información filtrada a través de un proxy inverso implementado por los administradores.==

#### **Cloud Snooper Attack** 

==Ataque de espionaje en la nube. Los ataques de espionaje en la nube se desencadenan en los grupos de seguridad (GS) de AWS para comprometer el servidor objetivo y extraer datos confidenciales de forma sigilosa. Los atacantes realizan este ataque aprovechando un firewall mal configurado o cualquier vulnerabilidad subyacente. Utilizan diversas técnicas para eludir los controles de seguridad, como los firewalls, y obtener control remoto del servidor objetivo.== Los atacantes explotan una debilidad en los GS, que están diseñados para permitir solo el tráfico con los puertos de destino 80 o 443. Los atacantes instalan rootkits explotando debilidades en los filtros de tráfico, ataques a la cadena de suministro o ataques de fuerza bruta a SSH. Los atacantes transmiten sus paquetes de comando y control (C2) haciéndose pasar por tráfico legítimo. Posteriormente, el rootkit instalado intercepta...

#### **Golden SAML Attack** 

Ataque SAML Dorado. Los ataques SAML (Lenguaje de Marcado de Aserción de Seguridad Dorado) ==se implementan para atacar a proveedores de identidad en redes en la nube, como el Servicio de Federación de Active Directory (ADFS), que utilizan el protocolo SAML para la autenticación y autorización de usuarios. Inicialmente, los atacantes obtienen acceso administrativo al perfil de usuario del proveedor de identidad y explotan certificados de firma de tokens para generar tokens o respuestas SAML falsificados mediante la manipulación de las aserciones SAML.== Este acceso puede lograrse mediante secuestro de sesión, escalada de privilegios o movimiento lateral a través de vulnerabilidades o ataques previamente explotados.

#### **Living Off the Cloud Attack (LotC)**

Ataque de Vivir Fuera de la Nube (LotC)
==Living Off the Cloud (LotC) es una evolución moderna del ataque "living off the land", en el que los atacantes atacan las aplicaciones SaaS e IaaS de las víctimas para llevar a cabo actividades maliciosas como la exfiltración de datos. Dado que las organizaciones empresariales no pueden bloquear estos servicios en la nube, los ataques LotC se han convertido en vectores de ataque más prominentes. Lanzar un ataque LotC con éxito puede permitir a los atacantes robar datos confidenciales almacenados en la nube, minar criptomonedas, lanzar ataques DDoS y más.==

#### **▪ Session Hijacking using Cross-Site Scripting (XSS) Attack** 

 Los atacantes implementan XSS para robar las cookies utilizadas en el proceso de autenticación del usuario. Esto implica inyectar código malicioso en un sitio web, que posteriormente es ejecutado por el navegador. Con las cookies robadas, los atacantes explotan las sesiones activas del equipo, obteniendo así acceso no autorizado a los datos.

#### **▪ Session Hijacking using Session Riding**

Los atacantes explotan sitios web mediante falsificaciones de solicitudes entre sitios para transmitir comandos no autorizados. ==En el uso de Session Riding, los atacantes se aprovechan de una sesión activa enviando un correo electrónico o engañando a los usuarios para que visiten una página web maliciosa durante el inicio de sesión en un sitio objetivo real.== Cuando los usuarios hacen clic en el enlace malicioso, el sitio web ejecuta la solicitud como si el usuario ya la hubiera autenticado. Los comandos utilizados incluyen modificar o eliminar datos del usuario, realizar transacciones en línea, restablecer contraseñas, etc.

[^1]: **Cloud Service Provider**

[^2]: **Universal Description Discovery and Integrity** 

[^3]: **Simple Object Access Protocol**.

[^4]: **Web Services Description Language**

[^5]: **Managed Service Providers** 
