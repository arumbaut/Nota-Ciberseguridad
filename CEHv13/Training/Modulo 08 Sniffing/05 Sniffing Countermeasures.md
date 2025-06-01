Restringir el acceso físico a los medios de red para garantizar que no se pueda instalar un sniffer de paquetes:

Usar cifrado de extremo a extremo para proteger la información confidencial:

Agregar permanentemente la dirección MAC del gateway a la tabla ARP

Desactivar las transmisiones de identificación de red y, si es posible, restringir la red a usuarios autorizados para proteger la red de herramientas de sniffing:

Usar IPv6 en lugar de IPv4, ya que la implementación de IPsec es opcional en IPv4 pero obligatoria en IPv6:

**Sniffer Detection Techniques**

==▪ Ping Method Ñ: Enviar una solicitud de ping al equipo sospechoso en la red, utilizando su dirección IP y una dirección MAC incorrecta, si la máquina en cuestión está ejecutando un sniffer en modo promiscuo, no rechazará los paquetes con direcciones MAC diferentes, ya que el modo promiscuo permite que la máquina reciba todos los paquetes que circulan por la red.==

Asigna una MAC falsa a la IP víctima en tu tabla ARP: sudo arp -s 192.168.1.5 66:66:66:66:66:66

Luego haces ping a esa IP: ping 192.168.1.5

Si la víctima responde, es muy probable que esté en modo promiscuo, porque aceptó el paquete aunque no iba dirigido a su MAC real.

**▪ DNS Method**

Una técnicaadicional es enviar solicitudes ICMP (ping) a direcciones IP que no existen. Si algún equipo responde al ping, es posible que esté realizando búsquedas DNS inversas y, por tanto, esté ejecutando un sniffer.

**Promiscuous Detection Tools**

▪ Nmap Source: https://nmap.org

nmap --script=sniffer-detect [Target IP Address/Range of IP addresses]

▪ NetScanTools Pro Source: https://www.netscantools.com