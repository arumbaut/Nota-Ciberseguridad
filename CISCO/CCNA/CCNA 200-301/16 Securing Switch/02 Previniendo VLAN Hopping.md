- Tags: #switch #vlan_hopping #vlan_hopping_prevent

La VLAN nativa puede ser cualquiera que elijamos. La Vlan nativa por defecto es la Vlan1
Los puertos access port por defecto de los Switch es Vlan1 es decir por defecto los switchport access vlan es el 1


### Buenas pracicas 
**1 Evitar utilizar la Vlan 1**
**2 Cambiar la Vlan Nativa a una que no se utilice**
**3 Asignar switchport a cualquier Vlan excepto a la Vlan 1 y la Vlan nativa**

#### Vlan Nativa
El la Vlan donde el trafico se envia por un link trunkal sobre  802.1q sin tener que etiquetar la Vlan. Esta establecida por defecto como Vlan1 en dispositivos Cisco 