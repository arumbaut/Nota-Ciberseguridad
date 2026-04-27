- Tags: #router_add_ipv6

```cisco
RouterPrimario(config)#ipv6 unicast-routing #Nos permite crear una tabla de rutas IPV6

RouterPrimario(config)#interface fastethernet 0/0
RouterPrimario(config-if)#ipv6 address 2001:db8:4:a::1/64
RouterPrimario(config)#interface fastethernet 0/1
RouterPrimario(config-if)#ipv6 address 2001:db8:4:b::1/64
RouterPrimario(config)#exit
RouterPrimario#copy run start

```