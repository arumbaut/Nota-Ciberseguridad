
Esquema

![[Pasted image 20260419132248.png|631]]

Debemos primero configurar las interfaces que conectan a los SW en modo trunk para que se puedan propagar las VLANs. Otro punto por defecto cada Sw tiene configurado el modo VTP en modo server , esto permite que al configurar una VLAN en uno  todos los demás reciban la información como si fuera un cliente. Lo ideal es tener un servidor y los demás en modo cliente. También podemos resolver esto si ponemos un password al VTP para que los dispositivos clientes no agreguen la configuración automáticamente si no que necesiten de una aprobación

SW1
```cisco
Ver la conf VTP
sw1#show vtp status
sw1#configure terminal
sw1(config)#interface fastethernet 0/1
sw1(config-if)#switchport mode trunk
sw1(config)#exit
sw1(config)#interface fastethernet 0/2
sw1(config-if)#switchport mode trunk
sw1(config)#exit
sw1(config)#vtp domain cisco.local
sw1(config)#vtp password cisco
sw1(config)#vtp version 2  #Solo se puede hacer en modo server
sw1(config)#vlan 10
sw1(config-vlan)#name Produccion


```
SW2
```cisco
Ver la conf VTP
sw2#show vtp status
sw2#configure terminal
sw2(config)#interface fastethernet 0/1
sw2(config-if)#switchport mode trunk
sw2(config)#exit
sw2(config)#vtp version 2
sw2(config)#vtp mode client
sw2(config)#vtp domain cisco.local
sw2(config)#vtp password cisco

```
SW3
```cisco
Ver la conf VTP
sw3#show vtp status
sw3#configure terminal
sw3(config)#interface fastethernet 0/1
sw(config-if)#switchport mode trunk
sw3(config)#exit
sw3(config)#vtp version 2
sw3(config)#vtp mode client
sw3(config)#vtp domain cisco.local
sw3(config)#vtp password cisco
```