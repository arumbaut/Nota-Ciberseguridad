- Tag : #router_recovering

Lo que aremos es apagar el router conectados desde putthy
Lo primero es estando conectado al router 

![[Pasted image 20260406160003.png]]

Luego apagamos y encendemos el router y Cuando empicen a salir letras en la consola de putty volvemos realizar el paso 1 

![[Pasted image 20260406160003.png]]

```cisco
romom>confreg 0x2142 #ignora el fichero de start-config
romom>reset

esto nos preguntara una cosa le diremos que no  y nos dea entrar a la conf del router sin necesidade pasword


RouterPrimario()#copy startup-config running-config
RouterPrimario()#config t
RouterPrimario(config)#enable secret cisco
RouterPrimario(config)#exit
RouterPrimario(config)#config-register 0x2102
RouterPrimario(config)#exit
RouterPrimario#copy run start



```