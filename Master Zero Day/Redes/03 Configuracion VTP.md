- Tags : #vlan #vtp

 **VTP (VLAN Trunking Protocol)** : Es un protocolo propietario de Cisco que sirve para centralizar la gestión de las VLANs en una red. Básicamente permite crear un servidor VTP en un switch que distribuye todas las **VLANS** entre los switch de a red evitando la necesidad de tener que crear cada interface en cada switch

```cisco
# sw1 sera el switch servidor 
sw1>enable
sw1#configure terminal
sw1(config)#vtp mode server
sw1(config)#vtp domain mired.com
sw1(config)#vtp password lolo@1234



# sw2 sera el switch cliente 
sw1>enable
sw1#configure terminal
sw1(config)#vtp mode cliente
sw1(config)#vtp domain mired.com
sw1(config)#vtp password lolo@1234

# Esto hara que si creamos una vlan en el switch servidor (sw1) tambien se replicara a (sw2) 
```