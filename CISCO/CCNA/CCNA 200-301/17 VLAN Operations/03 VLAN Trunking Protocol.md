
Cuando se envía un paquete a través de un puerto trunk lo que ocurre es esto:

![[Pasted image 20260412161912.png|689]]

Se crea un paquete 
![[Pasted image 20260412162045.png|685]]

Al pasar por el puerto 1 como este pertenece a la VLAN 10 pues se modifica el frame agregándole la Vlan id 
![[Pasted image 20260412165403.png|773]]

Pasa por el puerto trunk que es el encargado de permitir las diferente Vlans en los dispositivos y al llegar al otro SW quita la etiqueta y lo envía a la Vlan especificada a la ip correspondiente
![[Pasted image 20260412165629.png|735]]

Configurando un enlace trunk entre 2 SW

```cisco
Switch1

switch1>enable
switch1#configure terminal
switch1(config)#vlan 10
switch1(config-vlan)#name LEFT
switch1(config-vlan)#exit
switch1(config)#vlan 20
switch1(config-vlan)#name RIGTH
switch1(config-vlan)#exit
switch1(config)#int f0/1
switch1(config-if)#switchport mode access
switch1(config-if)#switchport access vlan 10
switch1(config-if)#exit
switch1(config)#int f0/2
switch1(config-if)#switchport mode access
switch1(config-if)#switchport access vlan 20
switch1(config-if)#exit
switch1(config)#int f0/24
switch1(config-if)#switchport mode trunk
switch1(config-if)#switchport trunk allowed vlan 10,20
switch1(config-if)#exit
```


```cisco
Switch2

switch2>enable
switch2#configure terminal
switch2(config)#vlan 10
switch2(config-vlan)#name LEFT
switch2(config-vlan)#exit
switch2(config)#vlan 20
switch2(config-vlan)#name RIGTH
switch2(config-vlan)#exit
switch2(config)#int f0/1
switch2(config-if)#switchport mode access
switch2(config-if)#switchport access vlan 10
switch2(config-if)#exit
switch2(config)#int f0/2
switch2(config-if)#switchport mode access
switch2(config-if)#switchport access vlan 20
switch2(config-if)#exit
switch1(config)#int f0/24
switch1(config-if)#switchport mode trunk
switch1(config-if)#switchport trunk allowed vlan 10,20
switch1(config-if)#exit
switch1(config)#exit
switch1#show interface trunk


```

