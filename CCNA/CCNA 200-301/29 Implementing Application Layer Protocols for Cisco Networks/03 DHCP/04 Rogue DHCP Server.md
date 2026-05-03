- Tags: #rogue_dhcp

**Rogue DHCP Server** : Es cuando alguien agrega a nuestra red un servidor DHCP no autorizado, que ocurre con esto que cuando las maquinas clientes van a solicitar una dirección IP por primera vez envían un mensaje DHCP discovery que es un mensaje broadcast y los switch lo propagan por todas las interfaces entonces si ocurre que el servidor no autorizado responde antes que el Real pues se nos crea un problema de seguridad ya que la maquina cliente estará pasando atraves de este servidor no autorizado o donde le indique este servidor . 


Para resolver esto necesitamos en nuestros Switches debemos configurar los puertos de confianza por el que si se podrán recibir los DHCP Offer y DHCP ACK Messages asegurando así la red 

![[Pasted image 20260430135354.png]]


![[Pasted image 20260430144737.png]]


```cisco 

Switch>enable
Switch#configure terminal

Activamos el dhcp snooping
Switch(config)#ip dhcp snooping

Esto es neceario porque algunos servidores no pueden manejar la opcion 82 que es info que viene desde el SW y descarta el paquete

Switch(config)#no ip dhcp snooping information option
Switch(config)#interface gigabitEthernet 0/1
Switch(config-if)#ip dhcp snooping trust


```