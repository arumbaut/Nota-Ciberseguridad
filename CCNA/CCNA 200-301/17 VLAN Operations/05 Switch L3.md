- Tags: #switch_l3

Switch Virtual Interface: Es una interface virtual de capa 3 en el este tipo de SW que no tiene un puerto físico asignado.

Para que un SW L3 comience a hacer funciones de L3 hay que comunicárselo porque por defecto esta opción no esta habilitada por lo que se comporta como un SW L2

Partiendo de que ya tenemos este escenario configurado , procedemos a configurar la parte del enrutamiento en le SW L3. Las vlan u la asignacion de vlan a una interface se hace de la misma forma que en los SW L2 , como en apuntes anteriores [[02 VLAN Configurations]]

![[Pasted image 20260417103454.png|820]]

```cisco
Habilitamos la capacidad de enrutar paquetes
SWL3(config)#ip routing

Creamos las Virtual Interfaces y le asignamos una up
SWL3(config)#interface vlan 10
SWL3(config-if)#ip address 10.0.0.1 255.255.255.0
SWL3(config-if)#exit
SWL3(config)#interface vlan 20
SWL3(config-if)#ip address 192.168.0.1 255.255.255.0
SWL3(config-if)#exit
```

#swl3_asignar_ip_a_interface_fisica
Para que una interface de un SW L3 no se comporte como una interface de SW hay que hacerle un tratamiento para que nos permita asignarle una ip a la Interface
```cisco 
L3-SW(config-if)#no switchport
```