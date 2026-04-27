- Tags : #router_ssh_conf

Se utiliza para poder obtener acceso remoto al router de forma segura. Porque no siempre estaremos cerca del dispositivo para conectarnos por consola.

Para hacer esto es necesario haber configurado anteriormente un **hostname y yn domain-name** para poder generar la ssh key

```cisco
#Genera una clave criptografica en el standar RSA 
RouterPrimario(config)#crypto key generate rsa general-keys 

Nos pedira algunas cosas com :
Tamaño de la key  mientras mayor es mas segura es

Una vez terminada indicamos la version de ssh que utilizaremos

RouterPrimario(config)#ip ssh version 2

Ahora tenemos que crear el usuario que va a utilizar essta conexion ssh

RouterPrimario(config)#username admin secret cisco 

Ahora le diermos al router que permita esta conexion ssh para ello lo haremos en la vty. Podemos tenet 808 conexions virtuales simultaneas en el router pero solo habilitaremos las necesarias

RouterPrimario(config)#line vty 0 4  #Permite 5 conexiones virtuales
RouterPrimario(config-line)#transpot input ssh
RouterPrimario(config-line)#login local #Le indicamos que use la passw DB local
RouterPrimario(config-line)#logging sync

```