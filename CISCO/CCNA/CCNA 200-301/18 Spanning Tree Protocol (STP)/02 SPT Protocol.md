- Tags: #spt 

Procedimiento para implementar el SPT en la red

![[Pasted image 20260417123515.png|570]]

En términos de SPT  Bridge y Switch significan lo mismo

Para seleccionar el Root Bridge (SW) necesitamos un mecanismo para transferir información entre los sw , por lo que enviaremos pequeños mensajes llamados *BPDU (Bridge Protocol Data Unit)*, dentro de estos enviaremos información que nos permitirá seleccionar el Root Bridge , el mejor camino y que puerto debemos bloquear

![[Pasted image 20260417124027.png|721]]

El Bridge ID esta conformado de 2 partes y dentro de este el Priority también. 

![[Pasted image 20260417124415.png|693]]

![[Pasted image 20260417124835.png]]

## STP PORT COST

![[Pasted image 20260417124903.png]]


![[Pasted image 20260417125048.png|851]]

![[Pasted image 20260417125133.png|762]]

```cisco
Mostrar la configuracion del spanning-tree
sw#show spanning-tree

Cambiar la prioridad de una vlan
sw(config)#spanning-tree vlan 1 priority      #Priority 0 - 61440


Para ver los logs generados por spanning-tree
sw#debug spanning-tree events


```

![[Pasted image 20260417131931.png]]