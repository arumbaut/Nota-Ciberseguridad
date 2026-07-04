En Switch

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
interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
```