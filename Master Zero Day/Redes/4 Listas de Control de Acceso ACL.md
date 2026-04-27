- Taggs: #acl

Una ACL es una serie de reglas o instrucciones ordenadas que se aplican a las interfaces de un equipo para **permitir** o **denegar** el paso de paquetes de datos. Se basan en criterios específicos como la dirección IP de origen, la dirección IP de destino, el protocolo (TCP, UDP, ICMP) o incluso el número de puerto.


Las acl las aplicamos en el router para determinar que trafico se autoriza o no acceder a un determinada red.

```cisco 
Router>enable
Router#configure terminal
Router(config)#ip access-list extended Direccion  #Cremos la ACL

#Establecemos las reglas que queremos , por default tiene deny ip any any
Router(config-ext-nacl)#permit ip 192.168.20.0 0.0.0.255 192.168.50.0 0.0.0.255
Router(config-ext-nacl)#permit ip 192.168.20.0 0.0.0.255 192.168.40.0 0.0.0.255

#Aplicamos la ACL a la interface que queremos se apliquen las reglas

Router(config)#interface gigabitEthernet 0/0.2
Router(config-subif)#ip access-group Direccion in
```