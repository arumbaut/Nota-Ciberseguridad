#### **Aircrack-ng Suite** 
**▪ Airbase-ng:** ==Captura el handshake WPA/WPA2== y puede actuar como un punto de acceso ad-hoc.  
**▪ Aircrack-ng:** ==Este programa es la herramienta estándar para romper claves WEP y WPA/WPA2 PSK.==  
**▪ Airdecap-ng:** ==Desencripta WEP/WPA/WPA2 y puede usarse para eliminar los encabezados inalámbricos de los paquetes Wi-Fi.==  
**▪ Airdrop-ng:** Este programa ==se utiliza para la desautenticación dirigida y basada en reglas de usuarios.==  
**▪ Aireplay-ng:** Es especialmente efectivo para ==recopilar vectores de inicialización (IVs WEP) y handshakes WPA, que luego pueden usarse con aircrack-ng para análisis y pruebas de seguridad de la red==.  
**▪ Airgraph-ng:** Este programa ==crea un gráfico de relaciones cliente–punto de acceso y de sondeos comunes a partir de un archivo generado por airodump.==
**▪ Airmon-ng:** Se utiliza para cambiar de modo gestionado a modo monitor en interfaces inalámbricas y viceversa.  
**▪ Airodump-ng:** Este programa se usa para capturar paquetes de tramas 802.11 en bruto y recopilar vectores de inicialización WEP (IVs).  
**▪ Airolib-ng:** Este programa almacena y administra listas de ESSID y contraseñas usadas en la ruptura de WPA/WPA2.  
**▪ Airtun-ng:** Crea una interfaz de túnel virtual para monitorear tráfico encriptado e inyectar tráfico arbitrario en una red.

#### **Ataque de suplantación de MAC del AP (MAC Spoofing Attack AP)**
Muchos programas y APs permiten configurar valores definidos por el usuario para las direcciones MAC y los SSID de los dispositivos AP. La suplantación de MAC de un AP es una técnica usada por atacantes para hacerse pasar por un punto de acceso inalámbrico legítimo, cambiando la dirección MAC de su dispositivo para que coincida con la del AP confiable.

**MAC Spoofing Tools** 
**▪ Technitium MAC Address Changer** 

##### **Ataque de envenenamiento ARP inalámbrico (Wireless ARP Poisoning Attack)**
Un ataque de envenenamiento ARP afecta a todos los hosts en una subred. Todas las estaciones asociadas a una subred afectada por un ataque de envenenamiento ARP son vulnerables, ya que la mayoría de los puntos de acceso actúan como puentes transparentes a nivel de capa MAC.

Attackers use Ettercap to identify the MAC addresses of the clients and routers for performing various attacks such as ARP poisoning, sniffing, and MITM attacks

#### **==Puntos de Acceso Falsos (Rogue APs) – Ataque de Rogue AP==**
Los puntos de acceso (APs) se conectan a las tarjetas de red de los clientes (NICs) autenticándose con la ayuda de los SSIDs. Los APs no autorizados (o falsos) pueden permitir que cualquier persona con un dispositivo compatible con 802.11 se conecte a una red corporativa. Un AP no autorizado puede otorgar a un atacante acceso a la red.
Son puntos de acceso inalámbricos que un atacante instala en una red sin autorización y que no están bajo la gestión del administrador de red. Estos APs falsos no están configurados con medidas de seguridad, a diferencia de los APs autorizados en la red inalámbrica objetivo. Por lo tanto, este AP falso puede proporcionar un acceso trasero (backdoor) a la red inalámbrica objetivo.

**Creation of a Rogue AP Using MANA Toolkit** 

**Evil Twin (Gemelo Malvado)**

Un _evil twin_ es un punto de acceso inalámbrico (AP) que finge ser un AP legítimo imitando su SSID. Representa un peligro claro y presente para los usuarios de redes inalámbricas tanto privadas como públicas (WLANs).

Un atacante instala un AP falso fuera del perímetro de la red y atrae a los usuarios para que se conecten a este AP. El atacante utiliza herramientas como **KARMA**, que monitorea las solicitudes de sondeo (probes) de las estaciones para crear un _evil twin_. La herramienta KARMA escucha pasivamente los marcos de solicitud de sondeo inalámbricos y puede adoptar cualquier SSID comúnmente utilizado como propio, con el fin de atraer a los usuarios.

**Ataque de Reinstalación de Claves (KRACK)**

El **ataque de reinstalación de claves (KRACK)** explota fallos en la implementación del proceso de _handshake_ de cuatro vías en el protocolo de autenticación WPA2, el cual se utiliza para establecer una conexión entre un dispositivo y un punto de acceso (AP).

Todas las redes Wi-Fi seguras utilizan este proceso de _handshake_ de cuatro vías para establecer conexiones y generar una clave de cifrado nueva que se usará para proteger el tráfico de red.

**Ataque de Señal de Interferencia (Jamming Signal Attack)**

El **jamming** es un ataque realizado contra una red inalámbrica con el objetivo de comprometerla. En este tipo de explotación, grandes volúmenes de tráfico malicioso provocan una denegación de servicio (DoS) a los usuarios autorizados, obstruyendo el tráfico legítimo.

**Ataque aLTEr**

El ataque **aLTEr** se realiza generalmente en dispositivos LTE que cifran los datos del usuario en modo contador AES (AES-CTR), que no ofrece protección de integridad.

Para llevar a cabo este ataque, el atacante instala una torre de comunicación virtual (falsa) entre dos puntos finales auténticos para engañar a la víctima. El atacante usa esta torre virtual para interrumpir la transmisión de datos entre el usuario y la torre real, intentando secuestrar una sesión activa.

**Ataque Wi-Jacking**

Los atacantes utilizan un ataque de Wi-Jacking para obtener acceso a un gran número de redes inalámbricas. En este ataque, la información Wi-Fi de las víctimas cercanas puede ser obtenida sin usar ningún mecanismo de descifrado.

Este ataque puede ser efectivo cuando las credenciales están guardadas en el navegador de la víctima, cuando la víctima accede repetidamente al mismo sitio web, y cuando el router utiliza una conexión HTTP no encriptada para acceder a la interfaz de configuración del router desde el navegador.