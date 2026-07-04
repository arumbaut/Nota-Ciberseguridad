- Tags: #switch_basic_conf

```cisco
sw1>enable
sw1#configure terminal
sw1#hostname sw1
sw1(conf)#ip domain-name globalmantics.local
sw1(conf)#username admin secret cisco   #Crear user y pass local
sw1(conf)#enable secret cisco   #Habilitar el secret

#Habilitar ssh
sw1(config)#crypto key generate rsa general-keys modulus 1024
sw1(config)#ip ssh v 2
sw1(config)#line console 0
sw1(config)#login local
sw1(config-line)#line vty 0 4
sw1(config-line)#login local
sw1(config-line)#transport input ssh

```

Cambiar todas las interfaces de la VLA 1 y ponerla en otra ejem 10
```cisco
sw1(config)#ip default-gateway 10.0.0.1  #Poner un gateway por defeco al switch
sw1(config)#interface range fastEthernet 0/1 -24 , gigabitEthernet 0/1 - 2
sw1(config-if-range)#switchport mode access
#Apaga el la negociacion dinamica del protocolo Trunk
sw1(config-if-range)#switchport nonegotiate 


#Si la VLAN no esta creada la crea
sw1(config-if-range)#switchport access vlan 10  

#Le ponemos una direccion ip a la vlan para poder conectar al switch por ssh
sw1(config)#interface vlan 10
sw1(config-if)#ip address 10.0.0.2 255.255.255.0
sw1(config-if)no shutdown

 

#Apaga el protocolo SPT puede causar problmas de bucles cuando se conecta a otros equipos como switches
sw1(config-if-range)#spanning-tree portfast   


```

Salvamos las configuraciones
```cisco
sw1(config)#do copy run start
```

Las configuraciones de un switch se pueden utilizar en otro 
```cisco
sw1(config)show run 
```

Nos copiamos todo lo que nos da después del show run  , después de la version. Lo guardamos en un txt y esta configuración la podemos copiar directamente en la terminal de otro switch y se aplicarían  los mismos cambios. Se le harían unos retoques para que no entraran en conflicto estos.

Importante debemos agregar la habilitacion del ssh porque esto no se incluye en la copia de show run

`crypto key generate rsa general-keys modulus 1024`

El hosname y la direccion ip tambien serian necesarios depende de cada caso
