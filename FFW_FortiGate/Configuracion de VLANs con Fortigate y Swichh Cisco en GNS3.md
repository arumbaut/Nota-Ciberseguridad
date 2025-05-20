
#### Esta será nuestra arquitectura de red  en la cual crearemos 3 Vlan y les permitiremos comunicación 

![[image20250520092736.png]]
1- Configuraremos la interface del puerto 1 de nuestro FW para poder acceder a la interface WEB de administración 

**\#config system interface**
**\#edit port1**
**\#set mode dhcp**
**\#set role wan**
**\#set alias WAN**
**\#set allowacces https http ssh ping**
**\#show**

2- Entramos a nuestra interface web luego de ver la ip que se le asigno a nuestro puerto1 mediante el DHCP
**\# get system interface physical**

![[image20250520093633.png]]

Y nos iremos a las interfaces para por la interface del puerto2 que es por donde tendrán acceso las VLANs le crearemos cada 1 de las VLANs que necesitamos que para este caso les asignaremos VLAN2, VLAN3, VLAN4. 

![[image20250520094728.png]]

Una vez configurada cada una de las Vlans en el FW nos dirigimos a configurara el switch de cisco para que habilite las Vlans y les permita el paso además de crear modo trunkal para que permita el paso de las Vlans por el mismo puerto de salida.

**Switch>enable**
**Switch#configure terminal**
**Switch(config)#vlan 2**
**Switch(config-vlan)#name admin**
**Switch(config-vlan)#exit**
**Switch(config)#vlan 3**
**Switch(config-vlan)#name sistemas**
**Switch(config-vlan)#exit**
**Switch(config)#vlan 4**
**Switch(config-vlan)#name contabilidad**
**Switch(config-vlan)#exit**
**Switch(config-vlan)#end**
**Switch#show vlan brief**         COMANDO PARA MOSTRAR BREVEMENTE LAS VLAN QUE TENEMOS 

A continuacion configuraremos cada interface con su VLAN y configurar la interface que se conecta al FW configurarla en modo TRUNK 

Interface que conecta con el FW
**Switch#configure terminal**
**Switch(config)#interface G0/0**
**Switch(config-if)#switchport trunk encapsulation dot1q**
**Switch(config-if)#switchport mode trunk**
**Switch(config)#exit

Ahora configuramos las demás interfaces para dar acceso a sus vlans corresmpondientes
Interface de la VLAN2
**Switch#configure terminal**
**Switch(config-if)# interface G0/1**
**Switch(config-if)#switchport mode access**
**Switch(config-if)#switchport access vlan 2**

Esto para cada una de las interfaces a las que se conecta una maquina de la vlan

**Switch#configure terminal**
**Switch(config-if)# interface G0/2**
**Switch(config-if)#switchport mode access**
**Switch(config-if)#switchport access vlan 3**

**Switch#configure terminal**
**Switch(config-if)# interface G0/3**
**Switch(config-if)#switchport mode access**
**Switch(config-if)#switchport access vlan 4**

Luego verificamos que esten funcionando las configuraciones realizadas, nos vamos a una de las maquinas y hacemos una solicitud DHCP. Asi lo haremos con cada una de las PCs

PC1
**ip dhcp**

![[image20250520104658.png]]

Una vez comprobado que ya tenemos una ip le daremos acceso en las reglas del FW para permitir el trafico hacia la red externa. En esta interface nos creamos las reglas que permitiran el trafico , por defecto el FW tiene un regla implicita donde deniega todo el trafico .

![[image20250520110238.png]]

Y asi terminamos el ejercicio.