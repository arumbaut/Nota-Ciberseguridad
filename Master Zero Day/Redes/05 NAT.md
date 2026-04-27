- Tags : #nat #ccna 



![[Pasted image 20260325092500.png]]

Tablas de enutamiento para los routers

```cisco

R1

ip route 10.0.0.4 255.255.255.252 10.0.0.2
ip route 10.0.0.8 255.255.255.252 10.0.0.2
ip route 10.0.1.0 255.255.255.0 10.0.0.2
ip route 10.0.2.0 255.255.255.0 10.0.0.2
ip route 10.0.3.0 255.255.255.0 10.0.0.13
ip route 192.168.0.0 255.255.255.0 10.0.0.2
```

```Cisco 
R2


ip route 8.0.0.0 255.0.0.0 10.0.0.1
ip route 10.0.0.8 255.255.255.252 10.0.0.6
ip route 10.0.0.12 255.255.255.252 10.0.0.6
ip route 10.0.2.0 255.255.255.0 10.0.0.6
ip route 10.0.3.0 255.255.255.0 10.0.0.6

```

```cisco
R3

ip route 8.0.0.0 255.0.0.0 10.0.0.10
ip route 10.0.0.0 255.255.255.252 10.0.0.5
ip route 10.0.0.12 255.255.255.252 10.0.0.10
ip route 10.0.1.0 255.255.255.0 10.0.0.5
ip route 10.0.3.0 255.255.255.0 10.0.0.10
```

```Cisco

R4

ip route 8.0.0.0 255.0.0.0 10.0.0.14
ip route 10.0.0.0 255.255.255.252 10.0.0.9
ip route 10.0.0.4 255.255.255.252 10.0.0.9
ip route 10.0.1.0 255.255.255.0 10.0.0.9
ip route 10.0.2.0 255.255.255.0 10.0.0.9
```

Para aplicar el NAT debemos primeramente marcar las interfaces como outside e inside en cada caso . Tomaremos como ejemplo una sección de la la infraestructura general.

![](../../attachments/Pasted%20image%2020260325133711.png)

```cisco
R3

R3>enable
R3#configure terminal
R3(config)#interface gigabitEthernet 0/0
R3(config-if)#ip address 10.0.2.1 255.255.255.0   #Conf de la ip de la interface
R3(config-if)#no shutdown  #Levantamos la interface 
R3(config-if)#ip nat inside   #La marcamos como NAT inside ya que da de cara a la LAN

Hacemos lo mismo para el resto de las interaces

R3(config)#interface gigabitEthernet 0/1
R3(config-if)#ip address 10.0.0.9 255.255.255.252   #Conf de la ip de la interface
R3(config-if)#no shutdown  #Levantamos la interface 
R3(config-if)#ip nat outside  #La marcamos como NAT outside ya que da de cara a la WAN

R3(config)#interface gigabitEthernet 0/2
R3(config-if)#ip address 10.0.0.6 255.255.255.252   #Conf de la ip de la interface
R3(config-if)#no shutdown  #Levantamos la interface 
R3(config-if)#ip nat outside  #La marcamos como NAT outside ya que da de cara a la WAN
R3(config-if)#exit

Agregamos las rutas para que sepa a donde tiene que dirigir cada paquete dependiendo de la Red a la que va dirigido.

R3(config)#ip route 8.0.0.0 255.0.0.0 10.0.0.10   
R3(config)#ip route 10.0.0.0 255.255.255.252 10.0.0.5
R3(config)#ip route 10.0.0.12 255.255.255.252 10.0.0.10
R3(config)#ip route 10.0.1.0 255.255.255.0 10.0.0.5
R3(config)#ip route 10.0.3.0 255.255.255.0 10.0.0.10

Por ultimo configuramos la NAT que permitiremos.

Crearemos una acl para nuestra red local y aplicar la nat a esta regla.
R3(config)# access-list 1 permit 192.168.0.0 0.0.0.255

Aqui le decimos que aplique un nat a la interface interna y que lo que venga de la LAN le haga un NAT con la ip de la interface g0/1 IP 10.0.0.10
R3(config)# ip nat inside source list 1 interface g0/1 overload

```