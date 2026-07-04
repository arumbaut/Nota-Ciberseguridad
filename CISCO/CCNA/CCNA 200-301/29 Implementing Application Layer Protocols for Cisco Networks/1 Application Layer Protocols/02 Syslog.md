- Tags : #syslog 

Cuando se configura un servidor de syslog para que los dispositivos envíen los log a este , no es obligatorio pero si muy recomendable que se configure  la *Loop-back Interface*  en el router para que sea tomada como el *Router ID*  y este sea identificado y se guarde en el servidor de syslog con este identificador en vez de con alguna dirección random.

### Pasos 
1 - Configurar la Loop-back Interface
2 - Configurar el servidor de Syslog
3 - Configurar el dispositivo para que envíe los logs al servidor


### Configuración en router la loop-back para cada router
```cisco

B>enable
B#configure terminal
B(config)#interface loopback 0
B(config-if)#ip address 10.100.0.2 255.255.255.255
B(config-if)#

Si tenemos configuradas ruas debemos agregarla en nuestro caso tenemos OSPF asi que la agregamos aqui

B(config)#router ospf 10
B(config-router)#network 10.100.0.2 0.0.0.0 area 10
```

### Establecer el servidor de syslog para cada router
```cisco
A(config)#logging 10.0.0.12
A(config)#logging source-interface loopback 0 
```