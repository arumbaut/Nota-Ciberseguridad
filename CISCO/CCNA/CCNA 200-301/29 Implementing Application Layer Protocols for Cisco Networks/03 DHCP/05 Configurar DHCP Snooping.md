**DHCP Snooping** : en una opción que tienen los sw de cisco para indicarles por que puerto de confianza pueden recibir **DHCP Offer** evitando así que si algún actor malicioso conecta un servidor DHCP alternativo en nuestra red pues los equipos no tomen direcciones *IPs* de este si no del de confianza

Ejercicio para evitar **Rogue DHCP Server**    implementando **DHCP Snooping en el SW**


![[Pasted image 20260503222551.png]]

Configuración SW

```cisco
SwitchA>enable
SwitchA#configure terminal

###  Activamos DHCP Snooping ####
SwitchA(config)#ip dhcp snooping

#### Lo activamos en las Vlans que estemos utilizando, por motivos de seguridad recordadr que debemos quitar la Vlan 1 como Vlan por default en nuestro caso pusimos todos los puertos en la Vlan 10, este comando ademas pone todos los puertos en un estado de desconfianza automaticament   ###

SwitchA(config)#ip dhcp snooping vlan 10

#### Entramos al puerto por el cual se recibiran las DHCP Offer y le indicamos como puerto de confianza ####
SwitchA(config)#interface fastEthernet 0/24
SwitchA(config-if)#ip dhcp snooping trust
SwitchA(config-if)#exit

#### Por ultimo deshabilitamos la opcion information option ya que por lo general trae problemas con los servidores de DHCP evitando un correcto funcionamiento   ###
SwitchA(config)#no ip dhcp snooping information option


####  Mostramos las propiedades  ####
SwitchA(config)#do show ip dhcp snooping


#### Muestra una tabla con los dispositivos relacionados
SwitchA(config)#do show ip dhcp binding

```


![[Pasted image 20260503224432.png]]


Esta tabla la utilizamos cuando activamos **Dynamic ARP Inspection** [[03 Dynamic ARP Inspection]]
