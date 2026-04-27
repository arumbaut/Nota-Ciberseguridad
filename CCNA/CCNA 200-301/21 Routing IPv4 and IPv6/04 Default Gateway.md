Cuando ARP esta fuera de nuestra network el ip por el que preguntara sera el de nuestro default gateway esto lo hace la maquina mediante la tabla de ruteo interna que tiene.

Cuando se le indica una red Fuera de la red local pues el Paquete ARP se le agrega la direccion IP del Gaeway

En este escenario se intenta enviar un mensaje ICMP a la red 192.168.10.8. como no pertenece a la red local 10.0.0.0/24 pues busca en la tabla de ruteo el gateway por defecto y pregunta la MAC de este pues todos los mensajes que van a un red distinta de la local los enviara a este gatewar por defecto que no es mas que el router

![[Pasted image 20260421084021.png]]