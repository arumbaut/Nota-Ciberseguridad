
ARP utiliza un proceso de tres pasos para determinar y almacenar la dirección MAC de un host que se encuentre en la red local cuando se conoce solo la dirección IPv4 del host:

1. El host emisor crea una trama dirigida a una dirección MAC de difusión y la envía. En la trama hay un mensaje con la dirección IPv4 del host de destino que se desea encontrar.
2. Cada host de la red recibe la trama de difusión y compara la dirección IPv4 del mensaje con su dirección IPv4 configurada. El host con la dirección IPv4 coincidente envía su dirección MAC como respuesta al host emisor original.
3. El host emisor recibe el mensaje y almacena la información de la dirección MAC y la dirección IPv4 en una tabla, denominada tabla ARP.

Una vez que el host emisor tiene la dirección MAC del host de destino en su tabla ARP, puede enviar tramas directamente al destino sin realizar una solicitud ARP. Como los mensajes ARP dependen de tramas de difusión para entregar las solicitudes, todos los hosts de la red local IPv4 deben estar en el mismo dominio de difusión.