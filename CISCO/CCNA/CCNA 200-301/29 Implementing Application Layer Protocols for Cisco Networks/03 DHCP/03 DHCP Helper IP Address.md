- Tags : #dhcp_helper_ip_address

### IP Helper Address:
- Trabaja para varios protocolos incluidos el DHCP
- Es un mecanismo que tienen las interfaces de los routers para entender que van a recibir una petición DHCP Discovery Message y cuando la reciban  van a hacer un reenvío a nuestro servidor DHCP donde quier que este exista en nuestra red

![[Pasted image 20260430104648.png|732]]

Cuando un cliente hace una petición DHCP Discover esta viaja al router y el router hara un cambio de la Destination IP address del DHCP Discover Message

## Implementando DHCP IP Helper Address

Diagrama
![[Pasted image 20260430110918.png|743]]


### Primero configuramos el Router que hara de DHCP 

# Nota super importante: Es primordial tener bien configuradas las rutas porque si no se pierde el paquete y nunca llega a asignar el IP a los clientes . En este caso implementamos el Enrrutamiento Dinámico EIGRP

```cisco
Como nuestro servidor no esta conectado directamente a las redes que le pediran DHCP hay que ener en cuenta excluir las ip del router que si estara conectado a esa red porque si no creamos un conflicto de red

Router(config)#ip dhcp excluded-address 10.0.0.1
Router(config)#ip dhcp excluded-address 192.168.0.1


Creamos los pool de direcciones para cada red
DHCP_SERVER(config)#ip dhcp pool 10.0.0.0
DHCP_SERVER(dhcp-config)#network 10.0.0.0 255.255.255.0
DHCP_SERVER(dhcp-config)#default-router 10.0.0.1
DHCP_SERVER(dhcp-config)#dns-server 8.8.8.8

DHCP_SERVER(dhcp-config)#exit
DHCP_SERVER(config)#ip dhcp pool 192.168.0.0
DHCP_SERVER(dhcp-config)#network 192.168.0.0 255.255.255.0
DHCP_SERVER(dhcp-config)#default-router 192.168.0.1
DHCP_SERVER(dhcp-config)#dns-server 8.8.8.8

Configurando el enrrutamiento
DHCP_SERVER(config)#router eigrp 10
DHCP_SERVER(config-router)#no auto-summary
DHCP_SERVER(config-router)#network 172.16.1.0 0.0.0.255
```

### Ahora toca ir al router que esta conectado a la red para configurar la DHCP Helper IP Address

```cisco
Nos conectamos a la interface de cara a la red que solicitara DHCP y ponemos la ip helper address para cada inerface que solicite DHCP

A(config)#interface gigabitEthernet 0/0
A(config-if)#ip helper-address 172.16.1.68

A(config-if)#exit

A(config)#interface gigabitEthernet 0/1
A(config-if)#ip helper-address 172.16.1.68

Configurando el enrrutamiento
A(config)#router eigrp 10
A(config-router)#network 10.0.0.0 0.0.0.255
A(config-router)#network 192.168.0.0 0.0.0.255
A(config-router)#network 172.16.1.0 0.0.0.255
```