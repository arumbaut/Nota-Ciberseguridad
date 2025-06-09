 **Service Hijacking using Social Engineering** 
==En el secuestro de cuentas o servicios, un atacante roba las credenciales de un CSP o de un cliente mediante phishing, pharming, ingeniería social y explotación de vulnerabilidades de software. Con las credenciales robadas, el atacante obtiene acceso a los servicios de computación en la nube y compromete la confidencialidad, integridad y disponibilidad de los datos.==

**Service Hijacking using Network Sniffing** 
El rastreo de red implica la interceptación y monitorización del tráfico de red entre dos nodos de la nube. Los datos confidenciales sin cifrar (p. ej., credenciales de inicio de sesión) durante la transmisión a través de una red corren un alto riesgo. Los atacantes utilizan rastreadores de paquetes (p. ej., Wireshark) para capturar datos confidenciales, como contraseñas y cookies de sesión, y otros datos de configuración de seguridad relacionados con servicios web

 **Side-Channel Attacks or Cross-guest VM Breaches** 
Ataques de canal lateral o vulneraciones de máquinas virtuales entre huéspedes. ==Los atacantes pueden comprometer la nube colocando una máquina virtual maliciosa cerca de un servidor en la nube objetivo y luego lanzando un ataque de canal lateral==.  El atacante ejecuta la máquina virtual en el mismo host físico que la máquina virtual objetivo y aprovecha los recursos físicos compartidos . Luego, lanza ataques de canal lateral para extraer claves criptográficas/secretos de texto plano y robar las credenciales de la víctima.

**Wrapping Attack** 
==En un ataque de envoltorio, el engaño al adversario se produce durante la traducción del mensaje SOAP en la capa TLS. El atacante duplica el cuerpo del mensaje y lo envía al servidor como si fuera un usuario legítimo. El servidor comprueba la autenticación mediante el valor de la firma (que también está duplicado) y verifica su integridad. Como resultado, el adversario puede invadir la nube y ejecutar código malicioso para interrumpir el funcionamiento normal de los servidores en la nube.==

#### **Man-in-the-Cloud (MITC) Attack** 
==Los ataques MITC son una versión avanzada de los ataques MITM. En estos ataques, el atacante utiliza un exploit que intercepta y manipula la comunicación entre dos partes, mientras que los ataques MITC se llevan a cabo abusando de servicios de sincronización de archivos en la nube, como Google Drive o DropBox, para la vulneración de datos, el comando y control (C&C), la exfiltración de datos y el acceso remoto==

**Cloud Hopper Attack** 
==Ataque de salto de nube. Los ataques de salto de nube se desencadenan contra proveedores de servicios gestionados ([^5]MSP) y sus clientes. Una vez implementado con éxito, los atacantes pueden obtener acceso remoto a la propiedad intelectual e información crítica del MSP objetivo y sus usuarios/clientes globales. Los atacantes también se mueven lateralmente en la red, de un sistema a otro en el entorno de nube, para obtener mayor acceso a datos confidenciales de entidades industriales, como manufactura, organismos gubernamentales, atención médica y finanzas.== Los atacantes inician correos electrónicos de phishing selectivo con malware personalizado para comprometer las cuentas de usuario de empleados o empresas de servicios en la nube y obtener información confidencial.

#### **Cloud Cryptojacking** 
==El criptojacking consiste en el uso no autorizado del ordenador de la víctima para extraer criptomonedas de forma sigilosa. Los ataques de criptojacking son muy lucrativos e involucran tanto a atacantes externos como a infiltrados internos. Para llevar a cabo este ataque, los atacantes aprovechan vectores de ataque como configuraciones incorrectas en la nube, sitios web comprometidos y vulnerabilidades del lado del cliente o del servidor==.

**Cloudborne Attack**
Cloudborne es una vulnerabilidad que reside en un servidor en la nube físico que permite a los atacantes implantar una puerta trasera maliciosa en su firmware. La puerta trasera instalada puede persistir incluso si el servidor se reasigna a nuevos clientes o empresas que lo utilizan como IaaS. 

**Cloud Snooper Attack** 
Los ataques de espionaje en la nube se desencadenan en los grupos de seguridad (GS) de AWS para comprometer el servidor objetivo y extraer datos confidenciales de forma sigilosa. Los atacantes realizan este ataque aprovechando un firewall mal configurado o cualquier vulnerabilidad subyacente. Utilizan diversas técnicas para eludir los controles de seguridad, como los firewalls, y obtener control remoto del servidor objetivo. 

 **Golden SAML Attack** 
. Los ataques SAML (Lenguaje de Marcado de Aserción de Seguridad Dorado) se implementan para atacar a proveedores de identidad en redes en la nube, como el Servicio de Federación de Active Directory (ADFS), que utilizan el protocolo SAML para la autenticación y autorización de usuarios. 

** Session Hijacking using Cross-Site Scripting (XSS) Attack** 
 Los atacantes implementan XSS para robar las cookies utilizadas en el proceso de autenticación del usuario. Esto implica inyectar código malicioso en un sitio web, que posteriormente es ejecutado por el navegador. Con las cookies robadas, los atacantes explotan las sesiones activas del equipo, obteniendo así acceso no autorizado a los datos.

 **▪ Session Hijacking using Session Riding**
Los atacantes explotan sitios web mediante falsificaciones de solicitudes entre sitios para transmitir comandos no autorizados. ==En el uso de Session Riding, los atacantes se aprovechan de una sesión activa enviando un correo electrónico o engañando a los usuarios para que visiten una página web maliciosa durante el inicio de sesión en un sitio objetivo real.== Cuando los usuarios hacen clic en el enlace malicioso, el sitio web ejecuta la solicitud como si el usuario ya la hubiera autenticado. 