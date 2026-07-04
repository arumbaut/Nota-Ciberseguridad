- Tags : #vlan 

Al agregar Vlans a nuestro SW cambia nuestra tabla de direcciones MAC se le agrega la coumban VLAN

![[Pasted image 20260412123925.png|855]]

![[Pasted image 20260412124244.png]]


```cisco
  
Switch>
Switch>enable
Switch#configure terminal
Switch(config)#vlan 10
Switch(config-vlan)#name left
Switch(config-vlan)#exit
Switch(config)#vlan 20
Switch(config-vlan)#name Rigth
Switch(config-vlan)#do show vlan

VLAN Name Status Ports

---- -------------------------------- --------- -------------------------------

1 default active Fa0/1, Fa0/2, Fa0/3, Fa0/4

Fa0/5, Fa0/6, Fa0/7, Fa0/8

Fa0/9, Fa0/10, Fa0/11, Fa0/12

Fa0/13, Fa0/14, Fa0/15, Fa0/16

Fa0/17, Fa0/18, Fa0/19, Fa0/20

Fa0/21, Fa0/22, Fa0/23, Fa0/24

Gig0/1, Gig0/2

10 left active

20 Rigth active

1002 fddi-default active

1003 token-ring-default active

1004 fddinet-default active

1005 trnet-default active

```


Asignar una Vlan a un puerto
```cisco

switch(config)#interface fastEthernet 0/10
switch(config-if)#switchport mode access
switch(config-if)#switchport access vlan 10
```

Mostrar tabla de direccion MAC

```cisco
switch#show mac address-table
switch#show mac address-table dynamic
switch#show flash:/

```

![[Pasted image 20260412143449.png]]

Para crear Vlan > 1006 

```cisco
switch(config)#vtp mode transparent
switch(config)#vlan 2000
switch(config-vlan)#name ext_Prueba
```