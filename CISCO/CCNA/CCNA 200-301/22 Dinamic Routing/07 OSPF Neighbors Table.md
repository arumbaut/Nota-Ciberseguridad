
![[Pasted image 20260424170833.png]]


![[Pasted image 20260424170936.png]]

![[Pasted image 20260424171200.png]]

Cuando tenemos este tipo de estructura y un Router detecta un link down este enviara un mensaje LSA a todos sus vecinos y cada uno de los vecinos enviara un mensaje LSA a todos sus vecinos provocando así una propaganción masiva de mensajes LSA que pueden inundar el dispositivo de L2. 

![[Pasted image 20260424172941.png|709]]

Para resolver este problema OSPF determina el ROUTER ID que se selecciona según los siguientes criterios  para cada uno de los routers en nuestra red de Broadcast

![[Pasted image 20260424172112.png]]

![[Pasted image 20260424172136.png]]

Establecer la Loopback
```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#interface loopback 0
RouterA(config-if)#ip address 1.1.1.1 255.255.255.255
RouterA(config-if)#exit
```

![[Pasted image 20260424172159.png]]

![[Pasted image 20260424174913.png]]

##### Una ves que tiene los Routers ID OSPF selecciona 2 Router , Router designado y Router designado de respaldo, esta elección ocurre atraves del router id, el que tenga el *Router id* mayor es seleccionado como el *Designated Router DR*, y el segundo con mayor *Router id* es seleccionado como *Backup Designated Router BDR*   

![[Pasted image 20260424175354.png]]


Lo que ocurre es que estos 2 routers el *DR* y *BDR* van a tener en la tabla de vecinos a todos los demas icluido a ellos y el resto de ruters solo tendra en su tabla de vecinos a *DR y BDR*

![[Pasted image 20260424175606.png]]


Cuando uno de los dos pierde la conexión o falla *DR o el BDR*  ospf se encarga de volver a buscar un sustituto basado en los mismo criterio del *Router ID mayor*  en caso de volver a conectarse el router en falla lo marca com *DR-Other  no se convierte en DR nuevamente*

![[Pasted image 20260424175932.png]]