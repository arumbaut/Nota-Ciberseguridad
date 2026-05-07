

*Dynamic ARP Inspection* utiliza la información de *DHCP Snooping*  par proteger la red en contra de *spoofed ARP messages*  


Configuración de *Dynamic ARP Inspection*  partiendo de que previamente hemos configurado [[05 Configurar DHCP Snooping]]

Seguiremos tomando con referencia esta infraestructura aunque vale resaltar que esta configuración no es posible en *Packet Tracer*. Solo la tomamos de referencia

![[Pasted image 20260503222551.png]]

```cisco
 ### Primero le diremos que confien en la interface y el ip que va a nuestro gateway ya que esta no estara en la table de DHCP snooping binding  ###
 
 
 SwitchA>enable
SwitchA#configure terminal
SwitchA(config)#interface fastEthernet 0/24
SwitchA(config-if)#ip arp inspection trust
SwitchA(config-if)#exit

### Indicamos la Vlan que estaremos Inspeccionando
SwitchA(config)#ip arp inspection vlan 10

#### Nos muestra tabla con la inspeccion de los paquetes #### 
SwitchA(config)#do show ip arp inspection
 
```