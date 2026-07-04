
Lo primero es habilitar el ssh en el router para hacer las pruebas desde una maquina cliente

```cisco

#####  Necesario para poder generar la crypto key para ssh  ####
Router(config)#hostname Router-Radius
Router-Radius(config)#ip domain-name radius.local

####  Indicamos que queremos utiliar la version 2 de ssh  ####
Router-Radius(config)#ip ssh version 2

#####  Generamos la key  ###
Router-Radius(config)#crypto key generate rsa general-keys modulus 1024

#### Creamos un usuario local para en caso de fallo del servidor de Radius ####
Router-Radius(config)#username admin secret cisco

#### Asignamos autenticacion local a la line console 0 ####
Router-Radius(config)#line console 0
Router-Radius(config-line)#login local

Router-Radius(config-line)#exit

#### Asignamos autenticacion local a la line vty 0 4 y probamos si esta bien la conexion ssh ####

Router-Radius(config)#line vty 0 4
Router-Radius(config-line)#login local
Router-Radius(config-line)#transport input ssh
Router-Radius(config-line)#exit

### Guardamos la config en el start  ####
Router-Radius(config)#do copy run start

```

Segundo configuramos la autenticacion de Radius

```cisco
Creamos un nuevo modelo de autenticacion
Router-Radius(config)#aaa new-model

Le ponemos el Nombre Radius-Service y especificamos que tipos de autenticacion utilizara [radius local]  es importante poner local para que en caso de estar caido el servidor de radio poder autenticar con las cuentas locales
 
Router-Radius(config)#aaa authentication login Radius-Service group radius local

Creamos la info del Servidor de Radius en el Equipo

Router-Radius(config)#radius server Radius-Server
Router-Radius(config-radius-server)#address ipv4 192.168.10.10

Le indicamos la key con la que se comunicara con el servidor
Router-Radius(config-radius-server)#key cisco

Router-Radius(config-radius-server)#exit

Asignamos el aaa new-model a las line que queremos que utilicen este tipo de autenticacion


Router-Radius(config)#line vty 0 4
Router-Radius(config-line)#login authentication Radius-Service
Router-Radius(config-line)#transport input ssh 
Router-Radius(config-line)#exit

Router-Radius(config)#line console 0
Router-Radius(config-line)#login authentication Radius-Service
Router-Radius(config-line)#exit

Router-Radius(config)#line aux 0
Router-Radius(config-line)#login authentication Radius-Service
Router-Radius(config-line)#exit


```