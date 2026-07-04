
Haremos esto antes de conectar un SW a un red con la configuración VTP establecida para evitar los desastres que puede generar este protocolo. La manera en que ejecutaremos esto es poniendo el SW en modo *transparent*

```cisco
sw2(config)#vtp mode transparent
```

Esto no elimina las VLANs que se habían configurado anteriormente pero lo que si hace es que restablece a 0 el *Revision Number* por lo que no dará problemas posteriores.

En los nuevos dispositivos de cisco tmbien se puede apagar en VTP

```cisco
sw2(config)#vtp mode off
```