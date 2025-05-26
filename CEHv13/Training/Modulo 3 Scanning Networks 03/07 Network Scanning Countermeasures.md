#### **Contramedidas contra el Ping Sweep**

▪ Configurar los **firewalls** para bloquear las solicitudes ICMP _echo_ entrantes provenientes de fuentes desconocidas o no confiables.  
▪ Utilizar **sistemas de detección de intrusos (IDS)** y **sistemas de prevención de intrusos (IPS)**, como **Snort** ([https://www.snort.org](https://www.snort.org)), para detectar y prevenir intentos de _ping sweep_.  
▪ Evaluar cuidadosamente el tipo de tráfico del **Protocolo de Mensajes de Control de Internet (ICMP)** que circula por las redes empresariales.  
▪ Terminar la conexión con cualquier host que envíe más de 10 solicitudes ICMP _ECHO_.
▪ Utilizar una **zona desmilitarizada (DMZ)** y permitir solo comandos como **ICMP ECHO_REPLY**, **HOST UNREACHABLE** y **TIME EXCEEDED** dentro de la DMZ.  
▪ Limitar el tráfico ICMP con **listas de control de acceso (ACLs)** solo a las direcciones IP específicas del proveedor de servicios de Internet (ISP).  
▪ Implementar **limitación de velocidad (rate limiting)** para los paquetes ICMP, con el fin de reducir la efectividad de los _ping sweeps_ y otras técnicas de escaneo basadas en ICMP.  
▪ Dividir la red en segmentos más pequeños y aislados. Esto limita el alcance de lo que un atacante puede descubrir mediante un _ping sweep_ y dificulta el movimiento lateral en caso de que la red sea comprometida.

#### **Port Scanning Countermeasures** 

▪ Configurar reglas en el firewall y en el sistema de detección de intrusos (IDS) para detectar y bloquear las sondas.  
▪ El firewall debe ser capaz de detectar las sondas enviadas por atacantes que utilizan herramientas de escaneo de puertos. No debe permitir el paso del tráfico simplemente inspeccionando el encabezado TCP; debe poder examinar los datos contenidos en cada paquete antes de permitir que el tráfico lo atraviese.  
▪ Ejecutar herramientas de escaneo de puertos contra los hosts de la red para determinar si el firewall detecta correctamente la actividad de escaneo de puertos.  
▪ Asegurarse de que el firmware del router, IDS y firewall estén actualizados con sus últimas versiones o lanzamientos.  
▪ Configurar firewalls comerciales para proteger la red contra escaneos de puertos rápidos y ataques de inundación SYN (SYN floods).  
▪ Los hackers utilizan herramientas como Nmap y realizan detección de sistema operativo para obtener detalles de un sistema remoto. Por ello, es importante emplear un IDS en estos casos. Snort ([https://www.snort.org](https://www.snort.org)) es una tecnología muy útil de detección y prevención de intrusiones, principalmente porque sus firmas están frecuentemente disponibles de autores públicos.

#### **Contramedidas contra Banner Grabbing**

- Mostrar banners falsos para engañar o confundir a los atacantes.    
- Desactivar servicios innecesarios en el host de la red para limitar la divulgación de información.    
- Utilizar herramientas de enmascaramiento de servidor para deshabilitar o cambiar la información del banner.    
- Eliminar encabezados HTTP innecesarios y datos de respuesta, y camuflar el servidor proporcionando firmas falsas. Esto también incluye la opción de eliminar extensiones de archivo como .asp y .aspx, que indican claramente que el sitio se ejecuta en un servidor Microsoft.    
- Para Apache 2.x con el módulo mod_headers, usar una directiva en el archivo httpd.conf para cambiar la información del encabezado del banner y establecer el servidor como “New Server Name”.    
- Alternativamente, cambiar la línea ServerSignature a ServerSignature Off en el archivo httpd.conf.    
- Deshabilitar los detalles del proveedor y la versión en los banners.    
- Modificar el valor de ServerTokens de Full a Prod en el archivo httpd.conf de Apache para evitar la divulgación de la versión del servidor.    
- Modificar el valor de RemoveServerHeader de 0 a 1 en el archivo de configuración UrlScan.ini ubicado en C:\Windows\System32\inetserv\Urlscan. Este método previene la divulgación de la versión del servidor.
