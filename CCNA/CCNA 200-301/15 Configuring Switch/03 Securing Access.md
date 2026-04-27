- Tags: #switch_seure_acces

[[02 Configuración Basica SW]]
### Asegurando el Acceso

```cisco
switch(config)#enable secret cisco
switch(config)#username admin secret cisco
switch(config)#service password-encryption
switch(config)#line console 0
switch(config-line)#password cisco
switch(config-line)#login
switch(config-line)#line vty 0 4
switch(config-line)#login local 
switch(config-line)#transport input ssh
switch(config)#crypto-key generate rsa
```

Al hacer login local estamos indicando que utilice el usuario y el password local que nos creamos de lo contrario utiliza el pass que creamos en el console o el vty 

### Configurando una IP para administración

Para esto creamos un SVI (Switch VLAN Interface). Esto hace que todos los puertos que estén en la VLAN 1 me permitan acceder por ssh claro esta para mas seguridad se debe configurar una VLAN especifica para esto
```cisco
switch(config)#interface vlan 1
switch(config-if)#ip address 10.0.0.5 255.255.255.0
switch(config-if)#no shutdown

```

### Salvamos las configuraciones
```cisco
switch#copy run start
```

![[Pasted image 20260407100322.png]]