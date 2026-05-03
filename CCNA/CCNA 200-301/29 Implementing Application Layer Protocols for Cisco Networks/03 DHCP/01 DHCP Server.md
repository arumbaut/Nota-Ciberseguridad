- Tags: #dhcp 

Como funciona

### EL cliente envía una DHCP Discover
![[Pasted image 20260430100552.png|643]]

### El servidor envia un DHCP Offer
![[Pasted image 20260430100646.png|665]]

### El cliente responde con una DHCP Request
![[Pasted image 20260430100736.png|673]]

### El servidor envía un DHCP ACK
![[Pasted image 20260430100852.png|672]]

### Ahora el cliente configura la IP , MASK , GATEWAY, DNS

### En medio de este proceso de configuracion el servidor DHCP crea un DHCP Binding que no es mas que una tabla donde pone la MAC del cliente con la Información DHCP Asignada
![[Pasted image 20260430101111.png|687]]