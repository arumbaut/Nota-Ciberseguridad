**Sistema de Detección de Intrusos (IDS)**

es un software de seguridad o un dispositivo de hardware utilizado para monitorear, detectar y proteger redes o sistemas contra actividades maliciosas; alerta de inmediato al personal de seguridad correspondiente al detectar una intrusión. Son extremadamente útiles, ya que supervisan continuamente el tráfico de entrada y salida de la red en busca de actividades sospechosas para detectar brechas de seguridad en el sistema o la red.Específicamente, analizan el tráfico en busca de firmas que coincidan con patrones de intrusión conocidos y emiten una alerta cuando se detecta una coincidencia. Los IDS pueden clasificarse en IDS activos y pasivos, dependiendo de su funcionalidad. Un IDS pasivo generalmente solo detecta intrusiones, mientras que un IPS activo no solo las detecta, sino que también las previene.

**Funciones principales de un IDS:**

▪ Un IDS recopila y analiza información desde el interior de un equipo o una red para identificar posibles violaciones de la política de seguridad, incluyendo accesos no autorizados y usos indebidos.  
▪ Un IDS también se conoce como un “sniffer de paquetes”, ya que intercepta paquetes que circulan a través de diversos medios y protocolos de comunicación, usualmente TCP/IP.  
▪ Los paquetes se analizan después de ser capturados.  
▪ Un IDS evalúa el tráfico en busca de intrusiones sospechosas y emite una alarma al detectar dichas intrusiones.

**Ubicación del IDS en la red**

Uno de los lugares más comunes para implementar un IDS es cerca del firewall. Dependiendo del tráfico que se desee monitorear, un IDS se coloca fuera o dentro del firewall para vigilar el tráfico sospechoso que se origina desde el exterior o el interior de la red. Cuando se ubica en el interior, el IDS es ideal si se encuentra cerca de una zona desmilitarizada (DMZ); sin embargo, la mejor práctica es utilizar una defensa en capas, implementando un IDS frente al firewall y otro detrás del firewall dentro de la red.

![](attachments/image20250601095857.png)