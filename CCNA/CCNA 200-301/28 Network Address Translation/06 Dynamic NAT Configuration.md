- Tags: #dynamic_nat_conf

![[Pasted image 20260428182030.png|795]]


```cisco
Router0>enable
Router0#configure termina

1 - Declaramos las interfaces internar y externas

Router0(config)#int f0/0
Router0(config-if)#ip nat inside
Router0(config-if)#exit
Router0(config)#int f0/1
Router0(config-if)#ip nat outside

Habiendo declarado las interfaces internar y externas necesitamos crear una ACL para especificar que paquetes pasaran por nuestro proceso de NAT

Esta ACL no se aplicara a una interface del Router si no a nuestro proceso de NAT para que nuestro proceso de NAT sepa cuales son las IPs validas para el network translation

2 - Creamos la ACL
Router0(config)#access-list 10 permit 10.0.0.0 0.0.0.255

3 - Declaramos nuestra regla NAT
Sintaxi = ip nat inside source list [acl creada] interface [Interface con la IP publica]  overload

Router0(config)#ip nat inside source list 10 interface f0/1 overload
```

## Ver la tabla de traducciones NAT

```cisco
Router0#show ip nat translations

Filtrado de resultaos
Router0#show ip nat translations | include 10.11.12.23
```

## Limpiar la tabla de NAT
```cisco
Router0#clear ip nat translation *
```