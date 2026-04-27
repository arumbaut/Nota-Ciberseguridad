- Tags: #rutas_dinamicas 

![[Pasted image 20260423181206.png|667]]


![[Pasted image 20260423181351.png|686]]

Exterior Gateway Protocol es el mecanismo en la que los ISP (Service Provider) enrrutan el trafico entre cada ISP 

![[Pasted image 20260423181726.png|703]]

**BGP** es el protocolo que utiliza internet para transferir rutas entre diferentes **ISP**, es considerado el **Procotocolo Vector de Camino**  si administramos *BGP* configuraremos redes donde tendremos un camino muy especifico. un control granular sobre como el protocolo distribuirá  el trafico. Podremos Implementar políticas de rutas con *BGP* que serán consistentes con los acuerdos hechos con otros proveedores. 


![[Pasted image 20260423182447.png|663]]

![[Pasted image 20260423182711.png|765]]

IGP Interior Gateway Protocol se divide en 2 categorías
1- *Vector de distancia Distance Vector  (Protocolos de Vector de Distancia DVP)*
	- Los *Routers*  intercambian las tablas de rutas periódicamente informándole a los Routers receptores cuan lejos esta una red la *Distancia* y que dirección tomar el *Vector*. Enseña a los Routers de su entorno como llegar a una red de destino.
	- Utiliza 2 algoritmos diferentes para calcular la mejor ruta a la red de destino *Bellman Ford o Diffusion Update Algorithnm*
2- *Link State   (Link State Protocols LSP)*   
	- Intercambia información de enlaces *Link Information*  con todos los *Routers*  en toda la *Red*,  informa a todos los routers del sistema del estado del link *Link State*
	- Tiípicamente utiliza el *Shortes Path First Algorithnm  SPF* , en el caso de *OSPF* se utiliza el algoritmo de Dykstras  


![[Pasted image 20260423183048.png|771]]


### Se pregunta en el examen del CCNA pero para fines practicos en la vida real lo que se plnatea es si utilizar EIGRP o OSPF no de si utilizar DVP o LSP
## Protocolos de Vector de Distancia
- *Routing Information Protocol (RIP)*
	- Version 1
		- Es un protocolo de enrutamiento con clase (class full), significa que no presta atención a la mascara de subred.
	- Version 2
		- Es un protocolo de enrutamiento sin clase (class less), significa que  presta atención a la mascara de subred.
 - *Interior Gateway Routing Protocol (IGRP)*
	 - Es un protocolo propietario de *CISCO*  no se utiliza en la actualidad,  era un protocolo de enrutamiento con clase, era muy lento 
- - *Enhanced Interior Gateway Routing Protocol (EIGRP)*
	- Es un protocolo mas sofisticado
	- Su comportamiento es muy similar al de un *Link State Protocol*
## Link State Protocols
- *Open Shortest Path First (OSPF)*
- *Intermediate System - Intermediate System  (IS-IS)*
	- Protocolo muy antiguo y los dos OSPF y IS-IS trabajan de manera muy similar 