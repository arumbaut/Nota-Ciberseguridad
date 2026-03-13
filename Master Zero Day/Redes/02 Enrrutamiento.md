- Tags : #redes #enrutamiento #dhcp 


Escenario
![](../../../attachments/Pasted%20image%2020260312173543.png)

**IPs** : 
#### Red1 : 192.168.0.0 /24
#### Red2: 192.168.1.0 /24
#### Red3: INTERNET

### Comandos de configuracion R1 (Router1)
Tener muy en cuenta las interfaces que conectan las redes una es a la LAN interna y la otra es al otro Router se aprecia en la Topología.

```cisco

Router>enable
Router#show running-config   #Muetra la configuracion que esta corriendo el SO
Router#configure terminal
Router(config)#hostname R1   #Asignamos un nombre al router

#Entramos a la inerface que queremos configurar conectada con el SWITSH Gig0/0
R1(config)#interface gigabitEthernet 0/0   
R1(config-if)#ip address 192.168.0.1 255.255.255.0     #Asignamos la ip
R1(config-if)#no shutdown    #Para levantar la interface por defecto down
R1(config-if)#exit

#Interface de conexion entre los routers Gig0/1 
R2(config)#interface gigabitEthernet 0/1
R2(config-if)#ip address 10.0.0.1 255.255.255.252     #Asignamos la ip
R2(config-if)#no shutdown    #Para levantar la interface por defecto down
R2(config-if)#exit



#Creamos el servicio dhcp 
R1(config)#ip dhcp pool LAN1   #Creamos el poll para el dhcp
R1(dhcp-config)#dns-server 8.8.8.8    #Servidor DNS que asignara el DHCP
R1(dhcp-config)#default-router 192.168.0.1  #Gateway que asignara el DHCP
R1(dhcp-config)#network 192.168.0.0 255.255.255.0  #Red de la cual sirve IPs
R1(dhcp-config)#exit

#Haremos una exclusion de IPs que no asignara automaticamente
R1(config)#ip dhcp excluded-address 192.168.0.1 192.168.0.10
R1(config)exit
R1#write memory   #Salvar la conf en memoria para que nos se borre si reiniciamos el router

```


### Comandos de configuracion R12(Router2) Misma idea con la otra red
Tener muy en cuenta las interfaces que conectan las redes una es a la LAN interna y la otra es al otro Router se aprecia en la Topología.

```cisco


Router>enable
Router#show running-config   #Muetra la configuracion que esta corriendo el SO
Router#configure terminal
Router(config)#hostname R2   #Asignamos un nombre al router

#Entramos a la inerface que queremos configurar conectada con el SWITSH Gig0/0
R2(config)#interface gigabitEthernet 0/0
R2(config-if)#ip address 192.168.1.1 255.255.255.0     #Asignamos la ip
R2(config-if)#no shutdown    #Para levantar la interface por defecto down
R2(config-if)#exit

#Interface de conexion entre los routers Gig0/1 
R2(config)#interface gigabitEthernet 0/1
R2(config-if)#ip address 10.0.0.2 255.255.255.252     #Asignamos la ip
R2(config-if)#no shutdown    #Para levantar la interface por defecto down
R2(config-if)#exit


#Creamos el servicio dhcp 
R2(config)#ip dhcp pool LAN1   #Creamos el poll para el dhcp
R2(dhcp-config)#dns-server 8.8.8.8    #Servidor DNS que asignara el DHCP
R2(dhcp-config)#default-router 192.168.1.1  #Gateway que asignara el DHCP
R2(dhcp-config)#network 192.168.1.0 255.255.255.0  #Red de la cual sirve IPs
R2(dhcp-config)#exit

#Haremos una exclusion de IPs que no asignara automaticamente
R2(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10
R2(config)exit
R2#write memory   #Salvar la conf en memoria para que nos se borre si reiniciamos el router

```



### Enrrutando las 2 redes en R1
```cisco

R1>enable
R1#configure terminal
R1(config)#ip route 192.168.1.0 255.255.255.0 10.0.0.2

#Que decimos aqui: Que todos los paquetes que busquen la red 192.168.1.0/24 los va a enviar a la ip 10.0.0.2 , que es la ip del router siguiente que si conoce cual es esa red pues tine ip en una de sus intefaces 192.168.1.1

```

### Haremos lo mismo en R2 porque si no no podrá devolver los paquetes la red
```cisco

R2>enable
R2#configure terminal
R2(config)#ip route 192.168.0.0 255.255.255.0 10.0.0.1

#Que decimos aqui: Que todos los paquetes que busquen la red 192.168.0.0/24 los va a enviar a la ip 10.0.0.1 , que es la ip del router siguiente que si conoce cual es esa red pues tine ip en una de sus intefaces 192.168.0.1
```

### Ahora pondremos las maquinas a que obtengan la red por DHCP

![450](../../../attachments/Pasted%20image%2020260312181513.png)

![469](../../../attachments/Pasted%20image%2020260312181559.png)




### Configuramos ahora el Router de Internet  R3

#### Aqui conectamos las interfaces Gig 0/0 a la red 8.8.8.0 y la interface  Gig 0/2 al router R1 que conecta nuestras redes LAN1 y LAN2

```cisco


Router>enable
Router#show running-config   #Muetra la configuracion que esta corriendo el SO
Router#configure terminal
Router(config)#hostname Internet   #Asignamos un nombre al router

#Entramos a la inerface que queremos configurar conectada al servidor
Internet(config)#interface gigabitEthernet 0/0
Internet(config-if)#ip address 8.8.8.1 255.0.0.0     #Asignamos la ip
Internet(config-if)#no shutdown    #Para levantar la interface por defecto down
Internet(config-if)#exit

#Interface de conexion entre los routers R1 y R3 , Gig0/2 
Internet(config)#interface gigabitEthernet 0/2
Internet(config-if)#ip address 172.16.0.1 255.255.0.0     #Asignamos la ip
Internet(config-if)#no shutdown    #Para levantar la interface por defecto down

#Debemos indicarle las rutas a las redes internas de LAN1 y LAN2 
Internet(config)#ip route 192.168.0.0 255.255.255.0 172.16.0.2
Internet(config)#ip route 192.168.1.0 255.255.255.0 172.16.0.2


Internet(config-if)#exit

Internet#write memory   #Salvar la conf en memoria para que nos se borre si reiniciamos el router
```


### Configuramos la nueva interface conectada a internet en R1
```cisco

#Interface de conexion entre los routers R1 y R3 , Gig0/2 
R1(config)#interface gigabitEthernet 0/2
R1(config-if)#ip address 172.16.0.2 255.255.0.0     #Asignamos la ip
R1(config-if)#no shutdown    #Para levantar la interface por defecto down

#Ahora agregamos la ruta comodin para que todo lo que no conozca lo envie al router de internet

R1(config)#ip route 0.0.0.0 0.0.0.0 172.16.0.1
R1(config-if)#exit
R1#write memory
```

### Otras notas :

#### Si queremos poner un a ruta por defecto en nuestro router , es decir si no conocemos una red pues que la envíe a otro lugar lo haremos de la siguiente manera
```cisco

R1(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.2

#Que decimos aqui , que cualquier ip con cualquier mascara la envie a 10.0.0.2 que esta debe conocer el camino dependiendo de su configuracion
```