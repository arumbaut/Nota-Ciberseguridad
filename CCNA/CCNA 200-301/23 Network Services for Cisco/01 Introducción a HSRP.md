- Tags : #hsrp #redundancy_routers


#### HSRP Hot Standby Router Protocol
- Es un protocolo propietario de cisco utilizado muy a menudo en redes proporciona *Redundancy Default Gateway*
- Existen otro protocolos similares para cumplir esta tarea como *VRRP Virtual Router Redundancy Protocol*

![[Pasted image 20260427110524.png|727]]

Tenemos 2 router que se encuentran en la misma red y crearemos una IP virtual para que responda el Router que este actualmente en el *estado de activo active* a las peticiones que se hagan a esta IP virtual el otro estará en un *estado de espera standby* por si el primero fallase este se activaría. Esto lo logramos dándole a cada router un prioridad. 

- Cuando el Router que esta activo cae por algún fallo el que esta en standby se pone en activo ya que constantemente están los 2 router intercambiando *HELLO MESSAGES* para ver el estado de cada uno . Cabe destacar que si el router que fallo se recupera nada cambia solo se pone este en el estado de *Standby*. Aunque se puede configurar el comportamiento para que siempre se active el router que tenga mayor prioridad. Para esto debemos habilitar una cosas llamada *PREEMPT*

Configuración :

```cisco
  
RouterA>enable
RouterA#configure terminal
RouterA(config)#interface g0/0
RouterA(config-if)#standby 10 ip 10.0.0.1  #Creamos la IP Virtual de HSRP
RouterA(config-if)#standby 10 priority 110  #Establecemos la prioridad al route
											por defecto es 100

RouterA(config-if)#standby 10 preempt  #Activamos PREEMPT para que siempre este
									  ativo el Router con mayor prioridad 
```

```cisco
  
RouterB>enable
RouterB#configure terminal
RouterB(config)#interface g0/0
RouterB(config-if)#standby 10 ip 10.0.0.1  #Creamos la IP Virtual de HSRP
RouterB(config-if)#standby 10 priority 90  #Establecemos la prioridad al route
											por defecto es 100

#No necesecitamos activar PREEMPT este solo lo activaremos en el router que queremos priorizar y que tendra la prioridad mas alta
```