**Countermeasures**

Una red ideal de alojamiento web debe diseñarse con tres segmentos: un segmento de Internet, un segmento de servidores seguros, que a menudo se llama zona desmilitarizada (DMZ), y una red interna. El primer paso para asegurar los servidores web es colocarlos por separado en la DMZ, que está aislada de la red pública y de la red interna de alojamiento web.

**Patches and Updates**

▪ Escanee en busca de vulnerabilidades existentes; aplique parches y actualice el software del servidor regularmente.  
▪ Antes de aplicar cualquier hotfix o parche de seguridad, lea y revise en conjunto toda la documentación relevante.  
▪ Aplique todas las actualizaciones, independientemente de su tipo, según sea necesario.  
▪ Pruebe los paquetes de servicio (service packs) y hotfixes en un entorno representativo que no sea de producción antes de implementarlos en producción.

**Countermeasures: Protocols**

▪ Bloquee todos los puertos innecesarios, el tráfico ICMP y los protocolos innecesarios.  
▪ Refuerce (harden) la pila TCP/IP y aplique constantemente los parches y actualizaciones de software más recientes al software del sistema.  
▪ Si se utilizan protocolos inseguros como Telnet, SMTP y FTP, tome las medidas apropiadas para proporcionar autenticación y comunicación segura, por ejemplo, mediante el uso de políticas IPsec.

**Countermeasures: Accounts**

▪ Elimine todos los módulos y extensiones de aplicaciones que no se utilicen.  
▪ Desactive las cuentas de usuario predeterminadas no utilizadas creadas durante la instalación del sistema operativo.  
▪ Al crear un nuevo directorio raíz web, otorgue los permisos NTFS apropiados (los mínimos posibles) a los usuarios anónimos del servidor web IIS para acceder al contenido web.

**Countermeasures: Files and Directories**

▪ Elimine archivos innecesarios dentro de los archivos .jar.  
▪ Elimine información de configuración sensible dentro del bytecode.  
▪ Evite mapear directorios virtuales entre dos servidores diferentes o a través de una red.  
▪ Supervise y verifique con frecuencia todos los registros de servicios de red, registros de acceso al sitio web, registros del servidor de base de datos (por ejemplo, Microsoft SQL Server, MySQL y Oracle) y registros del sistema operativo.

**How to Defend against Web Server Attacks**

Monitor all ports on the web server regularly to prevent unnecessary traffic toward the target web server.

**▪ Server Certificates**

▪ Utilice un protocolo novedoso que no dependa de terceros para la validación de certificados.  
▪ Permita que los dominios examinen directa y seguramente sus certificados utilizando credenciales de autenticación de usuario previamente establecidas.  
▪ Utilice una construcción criptográfica robusta que mejore la validación de la identidad del servidor y resuelva las limitaciones de las soluciones de terceros.

**Web Application Security Scanners**  

**▪ Syhunt Hybrid Source: https://www.syhunt.com**

**▪ N-Stalker X Source: https://www.nstalker.com**

▪ Invicti (https://www.invicti.com)

▪ Burp Suite (https://www.portswigger.net)

▪ Wapiti (https://wapiti-scanner.github.io)

▪ WebScarab (https://owasp.org)

▪ WPSec (https://wpsec.com)

▪ Tinfoil Web Scanner (https://www.tinfoilsecurity.com)

▪ Skipfish (https://code.google.com)

▪ Detectify (https://detectify.com)

▪ OpenTextTM FortifyTM On Demand (https://www.opentext.com)

**▪ OWASP Zed Attack Proxy (ZAP) (https://www.zaproxy.org)**

  

**Web Server Security Scanners**  

**▪ Qualys Community Edition Source: https://www.qualys.com**

▪ Observatory (https://observatory.mozilla.org)

▪ WordPress Security Scan (https://hackertarget.com)

▪ Web Vulnerability Scanner (https://pentest-tools.com)

▪ Nikto (https://cirt.net) ▪ ImmuniWeb (https://www.immuniweb.com)

  

**Web Server Malware Infection Monitoring Tools** 

▪ QualysGuard Malware Detection Source: https://www.qualys.com

▪ Sucuri Site Check (https://sitecheck.sucuri.net)

▪ SiteLock Malware Removal (https://www.sitelock.com)

▪ Quttera (https://quttera.com)

▪ Web Inspector (https://www.webinspector.com)

▪ SiteGuarding (https://www.siteguarding.com)

  

**Web Server Security Tools** 
▪ OpenText Fortify WebInspect Source: https://www.opentext.com

▪ Acunetix Web Vulnerability Scanner (https://www.acunetix.com)

▪ NetIQ Secure Configuration Manager (https://www.netiq.com)

▪ SAINT Security Suite (https://www.carson-saint.com)

▪ Sophos Intercept X for Server (https://www.sophos.com)

▪ UpGuard (https://www.upguard.com)

**Web Server Pen Testing Tools**

▪ CORE Impact Source: https://www.coresecurity.com

▪ Cobalt Strike (https://www.cobaltstrike.com)

▪ Fuxploider (https://github.com)

▪ Mitmprox (https://mitmproxy.org)

**Patch Management** **and Hotfixes**

Un parche es una pequeña pieza de software diseñada para corregir problemas, vulnerabilidades de seguridad y errores, así como para mejorar la usabilidad o el rendimiento de un programa informático o de sus datos de soporte. Un parche puede considerarse un trabajo de reparación para un problema de programación.

==**Hotfixes**==

==Un hotfix es un paquete utilizado para abordar un defecto crítico en un entorno en vivo y contiene una solución para un solo problema. Actualiza una versión específica del producto. Los hotfixes proporcionan soluciones rápidas y garantizan que los problemas se resuelvan. Aplique hotfixes a los parches de software en los sistemas de producción.==

Automated patch management process

▪ Detect: Usar herramientas para detectar parches de seguridad faltantes.

▪ Assess: Evaluar el(los) problema(s) y su gravedad asociada, mitigando los factores que puedan influir en la decisión.

▪ Acquire: Descargar el parche para realizar pruebas.

▪ Test: Instalar el parche primero en una máquina de prueba para verificar las consecuencias de la actualización.

▪ Deploy: Desplegar el parche en los equipos y asegurarse de que las aplicaciones no se vean afectadas.

▪ Maintain: Suscribirse para recibir notificaciones sobre vulnerabilidades cuando se reporten.

Installation of a Patch

**▪ Identifying Appropriate Sources for Updates and Patches**

² Crear un plan de gestión de parches que se ajuste al entorno operativo y a los objetivos empresariales.

² Encontrar actualizaciones y parches apropiados en los sitios oficiales de los proveedores de aplicaciones o del sistema operativo.

² El método recomendado para rastrear problemas relevantes para el parcheo proactivo es registrarse en los sitios oficiales para recibir alertas.

▪ Installation of a Patch

Users can access and install security patches via the World Wide Web. Patches can be installed in two ways.

² **Manual Installation:** In this method, the user downloads the patch from the vendor and installs it.

² **Automatic Installation:** In this method, applications use an auto update feature to update themselves.

**▪ Implementation and Verification of a Security Patch or Upgrade** 

² Antes de instalar cualquier parche, verifique la fuente.

² Utilice un programa adecuado de gestión de parches para validar las versiones de los archivos y los sumarios de verificación (checksums) antes de desplegar los parches de seguridad.

² La herramienta de gestión de parches debe ser capaz de monitorear los sistemas parcheados.

² El equipo de gestión de parches debe revisar actualizaciones y parches de manera regular.

**Patch Management Tools** 
▪ GFI LanGuard Source: https://www.gfi.com

▪ Symantec Client Management Suite (https://www.broadcom.com)

▪ Solarwinds Patch Manager (https://www.solarwinds.com)

▪ Kaseya Patch Management (https://www.kaseya.com)

▪ Software Vulnerability Manager (https://www.flexera.com)

▪ Ivanti Patch for Endpoint Manager (https://www.ivanti.com)