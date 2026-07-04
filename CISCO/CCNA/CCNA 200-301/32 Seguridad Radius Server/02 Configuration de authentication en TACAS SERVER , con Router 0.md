
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

Segundo configuramos la authentication de Tacacs

```cisco
Creamos un nuevo modelo de autenticacion
Router0(config)#aaa new-model

Le ponemos el Nombre Tacacs-Service y especificamos que tipos de autenticacion utilizara [tacas+ local]  es importante poner local para que en caso de estar caido el servidor de Tacacs poder autenticar con las cuentas locales
 
Router0(config)#aaa authentication login Tacacs-Service group tacacs+ local

Creamos la info del Servidor de Tacacs en el Dispositivo

Router0(config)#tacacs-server host 192.168.10.10 key cisco

Asignamos el aaa new-model a las line que queremos que utilicen este tipo de autenticacion


Router-Radius(config)#line vty 0 4
Router-Radius(config-line)#login authentication Tacacs-Service
Router-Radius(config-line)#transport input ssh 
Router-Radius(config-line)#exit

Router-Radius(config)#line console 0
Router-Radius(config-line)#login authentication Tacacs-Service
Router-Radius(config-line)#exit

Router-Radius(config)#line aux 0
Router-Radius(config-line)#login authentication Tacacs-Service
Router-Radius(config-line)#exit


```