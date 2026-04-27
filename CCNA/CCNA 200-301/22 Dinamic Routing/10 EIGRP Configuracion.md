- Tags : #eigrp_configuration

*Autonomous system number* : Tiene que ser el mismo en todos los routers que se implemente el protocolo EIGRP  , este numero se envía en los HELLO MESSAGES para intercambiar información, y deben coincidir para establecer la relación de vecinos.


```cisco 
Router(config)#router eigrp ?

<1-65535> Autonomous system number

Router(config)#router eigrp 10
Router(config-router)#network 10.0.0.12 0.0.0.3
Router(config-router)#network 10.0.0.4 0.0.0.3
Router(config-router)#network 192.168.2.0 0.0.0.255
Router(config-router)#no auto-summary  #En versione modernas de CISCO no es necesario pues esta en of por defecto

```

```cisco
RouterB(config)#router eigrp 10
RouterB(config-router)#network 10.0.0.4 0.0.0.3
RouterB(config-router)#network 10.0.0.8 0.0.0.3
RouterB(config-router)#network 10.0.2.0 0.0.0.255
RouterB(config-router)#network 10.0.3.0 0.0.0.255
RouterB(config-router)#no auto-summary

```

```cisco
RouterC(config)#router eigrp 10
RouterC(config-router)#network 10.0.0.0 0.0.0.3
RouterC(config-router)#network 10.0.0.8 0.0.0.3
RouterC(config-router)#network 192.168.2.0 0.0.0.255
RouterC(config-router)#no auto-summary

```

```cisco
L3-SW(config)#router eigrp 10
L3-SW(config-router)#network 10.0.0.12 0.0.0.3
L3-SW(config-router)#network 10.0.0.0 0.0.0.3
L3-SW(config-router)#network 10.0.1.0 0.0.0.255
L3-SW(config-router)#network 192.168.99.0 0.0.0.255
L3-SW(config-router)#no auto-summary

```