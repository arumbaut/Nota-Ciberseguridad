- Tags : #ospf_conf

Podemos tener multiples instancias de OSPF configurada por eso debemos asignarle un numero de instancia para así saber cual estamos configurando. este numero es local para el Router , es recomendable utilizar el mismo numero de instancia en todos los dispositivos que configuremos para evitar confusiones 

Al igual que rip debemos indicarle las redes que serviremos que también serán aquellas conectadas directamente al router con la diferencia que a esta red si le agregaremos la *Wildcard Mask*  que no es mas que converti la *Network Mask* a *Wildcard Mask*   que en el protocolo se conoce en el Protocolo OSPF.

Ademas debemos indicarle el Area 

![[Pasted image 20260424131608.png|785]]

```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#router ospf 10
RouterA(config-router)#network 10.0.0.0 0.0.0.3 area 0 (Hacia RouterA)
RouterA(config-router)#network 10.0.0.4 0.0.0.3 area 0 (Hacia RouterC)
RouterA(config-router)#network 192.168.0.0 0.0.0.255 area 0

RouterA#show ip protocols
```

```cisco
RouterB>enable
RouterB#configure terminal
RouterB(config)#router ospf 10
RouterB(config-router)#network 10.0.0.0 0.0.0.3 area 0 (Hacia RouterA)
RouterB(config-router)#network 10.0.0.8 0.0.0.3 area 0 (Hacia RouterC)
RouterB(config-router)#network 192.168.10.0 0.0.0.255 area 0

RouterB#show ip protocols
```

```cisco
RouterC>enable
RouterC#configure terminal
RouterC(config)#router ospf 10
RouterC(config-router)#network 10.0.0.4 0.0.0.3 area 0 (Hacia RouterA)
RouterC(config-router)#network 10.0.0.8 0.0.0.3 area 0 (Hacia RouterC)
RouterC(config-router)#network 192.168.20.0 0.0.0.255

RouterC#show ip protocols
```

## Comandos Útiles 

```cisco 
RouterC#show ip protocols  #Nos mustra que protocolos de enrrutamiento estan implementados

RouterC#show ip ospf neighbor  #Muestra los routers vecinos

Neighbor ID    Pri    State      Dead Time      Address     Interface

192.168.0.1     0     FULL/ -    00:00:35       10.0.0.5    Serial0/3/0

192.168.10.1    0     FULL/ -    00:00:30       10.0.0.9    Serial0/3/1



RouterC#show ip ospf database

OSPF Router with ID (192.168.20.1) (Process ID 10) 

Router Link States (Area 0) 

Link ID        ADV Router       Age      Seq#         Checksum     Link count

192.168.0.1    192.168.0.1      355     0x80000005    0x00e2d2       5
192.168.10.1   192.168.10.1     340     0x80000005    0x006f29       5
192.168.20.1   192.168.20.1     329     0x80000005    0x006219       5



RouterC#show ip ospf database router 


Resetear el proceso OSPF para que vuelva a btener u Router ID
RouterC#clear ip ospf process
```