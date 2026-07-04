 - Tags: #router_basic_conf 

#### Accediendo al Router

```cisco
#Entrando al modo de configuracion
router>enable
router>configure terminal
router(config)>

```

#### Configuraciones Básicas

```cisco
router>enable
router>configure terminal
router(config)>hostname RouterInformatica

#Creamos un nombre de dominio porque es necesario para posteriormente crear las key ssh
RouterInformatica(config)>ip domain-name loquesea.loca 

#Crear un banner o mensaje de bienvenida
RouterInformatica(configure)>banner motd #Solo personal autorizado
Este es el Admin
Acceso no autorizado sera castigado
#
 
```