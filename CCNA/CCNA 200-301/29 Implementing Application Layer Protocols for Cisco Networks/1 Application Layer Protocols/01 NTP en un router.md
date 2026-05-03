- Tags : #ntp #syslog 

#show_hora_router

Ejercicio

![[Pasted image 20260429201203.png]]

Ruter0 sera la configuracion del como ejemplo, es recomendable poner el router de cara a internet a que sincronice y ponerlo ademas como servidor NTP y los demas routers de la red interna pues que sincronicen de el porque de lo contrario puede traernos problemas con la tabla de NAT
```cisco
Mostrar la hora 

Router0#show clock
Router0#configure terminal
Router0(config)#clock ?

Esta parte es muy importante para que sincronice bien debes poner correctamente tu zona horaria y la de verano tambien en mi caso España
Router0(config)#clock timezone CET 1 0 
Router0(config)# clock summer-time CEST recurring last Sun Mar 2:00 last Sun Oct 3:00 

Ahora configuramos el servidor NTP al que nos conectaremos
Router0(config)# ntp server 198.51.100.10

Lo convertimos en servidor NTP para que los demas lo consulten
Router0(config)#ntp master 3

Ver las configuraciones resultantes
Router0#show clock
Router0#show ntp status
Router0#show ntp associations

```