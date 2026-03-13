- Tags : #redes #vlan

### Configuracion de las VLANs en el SWITCH
```cisco 

SW1>enable
SW1#configure terminal

SW1(config)#vlan 10
SW1(config-vlan)#name Ventas
SW1(config-vlan)#exit

SW1(config)#vlan 20
SW1(config-vlan)#name Marketimg
SW1(config-vlan)#exit

SW1(config)#vlan 30
SW1(config-vlan)#name IT
SW1(config-vlan)#exit
```

### Asignar puertos a VLANs
```cisco 

SW1>enable
SW1#configure terminal
#Configurar un rango de interfaces,  fastEthernet 0 de la 1 a la 4 - 4 interfaces 
SW1(config)#interface range fastEthernet 0/1-4 
SW1(config-if-range)#switchport mode access
SW1(config-if-range)#switchport access vlan 10
SW1(config-if-range)#exit

#Configurar un rango de interfaces,  fastEthernet 0 de la 5 a la 8 -3 interfaces
SW1(config)#interface range fastEthernet 0/5-8
SW1(config-if-range)#switchport mode access
SW1(config-if-range)#switchport access vlan 20

#Configurar un rango de interfaces,  fastEthernet 0 de la 9 a la 10 -2 interfaces 
SW1(config)#interface range fastEthernet 0/9-10
SW1(config-if-range)#switchport mode access
SW1(config-if-range)#switchport access vlan 30
SW1(config-if-range)#exit
SW1(config)#exit
SW1#write memory

Building configuration...

[OK]

SW1#
```


### Configurar enlace troncal con router  en el SWITCH en la interface conectada al Router  fastEthernet 0/24

Para poder conectar las VLANs es necesario enrrutar paquetes mediante un enrrutador para que estas se puedan comunicar entre si por lo que sera necesario que todas las VLANs puedan llegar al enrrutador por lo que es necesario un enlace Trunkal con este

```cisco

SW1(config)#interface fastEthernet 0/24
SW1(config-if)#switchport mode trunk
SW1(config-if)#switchport trunk allowed vlan 10,20,30
SW1(config-if)#exit
SW1(config)#exit
SW1#write memory

```

### Configurar el ROUTER 

#####  Configurar Subinterfaces
```cisco
#Creamos la subinterface para la VLAN 10
interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

#Creamos la subinterface para la VLAN 20
interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.20.1 255.255.255.0
exit

#Creamos la subinterface para la VLAN 30
interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.30.1 255.255.255.0
exit
```