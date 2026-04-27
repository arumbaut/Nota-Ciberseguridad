- Tags : #arp #arp_work


ARP es un protocolo que vive entre las capas *Data Link Layer y Network Layer* , lo que hace es enviar un mensaje donde pregunta por la MAC de una IP especifica. Pero como sabe a donde debe mandar este mensaje? Pues no lo sabe por lo que utiliza la *Direccion de Broadcast o direccion de Disfucion*  
MAC ($FF:FF:FF:FF:FF:FF$) se le conoce como **Dirección de Broadcast** (o dirección de difusión)

![[Pasted image 20260421072902.png|758]]

![[Pasted image 20260421073220.png|752]]

En respuesta la maquina que tiene la IP que buscamos pues responde con un paquete ARP

![[Pasted image 20260421073454.png|757]]

![[Pasted image 20260421073559.png|755]]

**Teniendo ya la Destination MAC Address pues completamos el FRAME**
[[01 IPv4 Packet]]