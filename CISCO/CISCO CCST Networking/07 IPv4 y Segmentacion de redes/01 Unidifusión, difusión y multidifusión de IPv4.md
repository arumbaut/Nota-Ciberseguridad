
### Unidifusión

La transmisión unidifusión (unicast) se refiere a un dispositivo que envía un mensaje a otro dispositivo en comunicaciones uno a uno.

Un paquete de unidifusión tiene una dirección IP de destino que es una dirección de unidifusión que va a un único destinatario. Una dirección IP de origen sólo puede ser una dirección de unidifusión, ya que el paquete sólo puede originarse de un único origen. Esto es independiente de si la dirección IP de destino es una unidifusión, difusión o multidifusión.

### Difusión Broadcast

Transmisión de transmisión hace referencia a un dispositivo que envía un mensaje a todos los dispositivos de una red en comunicaciones unipersonales.

Los paquetes de difusión tienen una dirección IPv4 de destino que contiene solo números uno (1) en la porción de host.

**Nota:** IPv4 utiliza paquetes de difusión. Sin embargo, no hay paquetes de difusión con IPv6.

Todos los dispositivos del mismo dominio de difusión deben procesar un paquete de difusión. Un dominio de difusión identifica todos los hosts del mismo segmento de red. Una transmisión puede ser dirigida o limitada. Una difusión dirigida se envía a todos los hosts de una red específica. Por ejemplo, un host de la red 172.16.4.0/24 envía un paquete a la dirección 172.16.4.255. Se envía una difusión limitada a 255.255.255.255. De manera predeterminada, los enrutadores no reenvían difusiones.


### Multidifusión IPv4

La transmisión de multidifusión reduce el tráfico al permitir que un host envíe un único paquete a un grupo seleccionado de hosts que estén suscritos a un grupo de multidifusión.

Un paquete de multidifusión es un paquete con una dirección IP de destino que es una dirección de multidifusión. IPv4 reservó las direcciones de 224.0.0.0 a 239.255.255.255 como rango de multidifusión.

Los hosts que reciben paquetes de multidifusión particulares se denominan clientes de multidifusión. Los clientes de multidifusión utilizan servicios solicitados por un programa cliente para subscribirse al grupo de multidifusión.

Cada grupo de multidifusión está representado por una sola dirección IPv4 de destino de multidifusión. Cuando un host IPv4 se suscribe a un grupo de multidifusión, el host procesa los paquetes dirigidos a esta dirección de multidifusión y los paquetes dirigidos a la dirección de unidifusión asignada exclusivamente.

Los protocolos de enrutamiento como OSPF utilizan transmisiones de multidifusión. Por ejemplo, los routeres habilitados con OSPF se comunican entre sí mediante la dirección de multidifusión OSPF reservada 224.0.0.5. Sólo los dispositivos habilitados con OSPF procesarán estos paquetes con 224.0.0.5 como dirección IPv4 de destino. Todos los demás dispositivos ignorarán estos paquetes.