- Tags: #extended_acl_conf

```cisco
Router(config)#ip access-list extended DEMO1


Router(config-ext-nacl)#permit tcp 10.0.0.16 0.0.0.1 host 192.168.10.10 eq 80

Router(config-ext-nacl)#permit icmp 10.0.0.16 0.0.0.1 host 192.168.10.10

Router(config-ext-nacl)#permit tcp host 10.0.0.128 host 192.168.10.10 eq 22

Router(config-ext-nacl)#deny ip any any

Router(config-ext-nacl)#exit

Router(config)#interface gigabitEthernet 0/0

Router(config-if)#ip access-group DEMO1 in
```

Si agregamos la palabra log al final de una regla nos guardara un log con el trafico que permite y deniega esta. Aunque puede ser util si nuestro router no tiene buena capacidad de procesamiento puede generar muchos problemas
Ejemplo
```cisco
Router(config-ext-nacl)#permit tcp host 10.0.0.128 host 192.168.10.10 eq 22 log

Router(config)#logging 10.0.0.16  #Indicamos al router el Logs Server
```

### Kiwi Syslog Server  para hacer pruebas.

