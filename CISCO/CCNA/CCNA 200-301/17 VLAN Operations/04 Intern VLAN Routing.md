- Tags : #vlan #vlan_routing 

![[Pasted image 20260415170326.png|664]]

Ejercicio a Realizar

![[Pasted image 20260415170801.png|663]]

Partimos de la base que tenemos configurado en el SW varias vlans y asignados a los puertos estas vlans con diferentes rangos ip , solo quedaria poner el elnace trunkal del SW al Router y configurar el Router para que tenga varias subinterfaces en el segmento de red de cada Vlan para poder enrutar paquetes de una Vlan a otra

```cisco
SW3750  En este tipo de sw se hace asi porque soporta varios tipos de encapsulamiento , los SW2960 solo dot1q

SW3750
sw1>enable
sw1#configure terminal
sw1(conf)#int g0/1
sw1(conf-if)#switchport trunk encapsulation dot1q
sw1(conf-if)#switchport mode trunk

SW2960
sw1>enable
sw1#configure terminal
sw1(conf)#int g0/1
sw1(conf-if)#switchport mode trunk
```


En Router

```cisco
#Creamos la subinterface para la VLAN 10
router1(config)#interface fastEthernet 0/0.10
router1(config-if)#no shutdown
router1(config-if)#exit
router1(config)#interface fastEthernet 0/0.10
router1(config-if)#encapsulation dot1Q 10
router1(config-if)#ip address 192.168.10.1 255.255.255.0
router1(config-if)#no shutdown
router1(config-if)#exit
```