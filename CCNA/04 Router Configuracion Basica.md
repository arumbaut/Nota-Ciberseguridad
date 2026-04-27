- Tags: #router_basic_conf 

```cisco

Router>enable
Router#show running-config   #Muetra la configuracion que esta corriendo el SO
Router#configure terminal
Router(config)#hostname R1 #Necesaria para generar las key de ssh
R1(conf)#ip domain-name globalmantics.local #Necesaria para generar las key de ssh
R1(conf)#username admin secret cisco   #Crear user admin y pass cisco `secret` hace que la contraseña se guarde oculta y encriptada. 

R1(conf)#enable secret cisco   #Pone contraseña (`cisco`) para cuando se escriba el comando `enable`

#Habilitar ssh
#Genera los certificados y llaves matemáticas con un tamaño de 1024
R1(config)#crypto key generate rsa general-keys modulus 1024

R1(config)#ip ssh version 2 #Fuerza al router a usar la versión 2 de SSH

R1(config)#line console 0  #Te mete en la configuración del cable físico (consola)

R1(config)#login local  #Cuando alguien se enchufe por cable, pídele el usuario y contraseña que creamos antes en la base de datos local

R1(config-line)#line aux 0 #Lo mismo que `line console 0` pero para el puerto Auxiliar (un puerto antiguo que se usaba para conectar módems telefónicos)

R1(config-line)#login local
R1(config-line)#line vty 0 4 #Te mete en las líneas virtuales (del canal 0 al 4, o sea, permite 5 conexiones a la vez)

R1(config-line)#login local

R1(config)#transport input ssh

```