

- Miraremos dentro de las **Cabeceras del  Paquete IP**
	- Dentro de este miraremos el *Source IP* y *Destination IP*
	- Utilizaremos estos 2 como criterio de selección para elegir unos paquetes sobre otros
	- Miraremos dentro de las *Cabeceras del Segmento TCP*  el *Source Port y el Destination Port* 
	- También con las *Cabeceras del Segmento UDP*  el *Source Port y el Destination Port* 

### Tenemos 2 Tipos de ACL 
- **Standard ACL**
	- Seleccionan los paquetes solo por su *IP de origen*
- **Extended ACL**
	- Seleccionan paquetes || segmentos mediante su *Protocolo* (IP, TCP, UDP)
	- Seleccionan por el *Source IP*
	- Seleccionan por *Destination IP*
	- Seleccionan por *Source Port*
	- Seleccionan por *Destination Port*

### En IPv6  no existen las Standard ACL solo las Extended ACL