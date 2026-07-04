- Tags : #router_conf_interface

Las interfaces es donde configuramos las direcciones IP del router

```cisco
RouterPrimario(config)#interface fastethernet 0/0 #Entramos en la conf de la interface 

#Configuramos la ip
RouterPrimario(config-if)#ip address 10.0.0.1 255.255.255.0
RouterPrimario(config-if)#no shutdown
```

Salver las configuraciones
```cisco
RouterPrimario#copy running-config startup-config
```