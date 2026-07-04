- Tags : #router_secure_acces #log_sync


Para asegurar el acceso al disppositivo debemos configurar el puerto de *console* y el puerto *aux*  

[[1 Configuracion Basica del Router]]
```cisco
#Agregar seguridad al console port y aux port

router>enable
router>configure terminal
router(config)#line console 0 #Nos accede a las conf del console port
router(config-line)#password cisco #Agrega password al console port
router(config-line)#login  #Indica que requiera el password al usuario
router(config-line)#line aux 0 #Entramos a la conf del aux port
router(config-line)#password cisco #Agrega password al aux port
router(config-line)#login  #Indica que requiera el password al usuario
router(config-line)#exit

#Agregar seguridad al modo privilegiado, si no hacemos esto no tendremos acceso al modo de configuracion desde otro puerto que no sea el de consola 
router(config)>enable secret cico #Agrega password al modo privilegiado

```

Hay una diferencia entre los enable secret y los passwords de los puertos de console y aux , estos últimos están escritos en texto plano y el otro encriptados.

Vamos  a encriptar también estos password para que nos se vean en texto claro a la hora de mostrar la configuración.

```cisco

router(config)#service password-encryption
```

Es común que es sistema nos arroje logs en la consola mientras escribimos , esto puede llegar a ser muy molesto lo arreglamos de la siguiente manera
```cisco
router(config)#line console 0 #Nos accede a las conf del console port
router(config-line)#loggin sync
router(config-line)#line aux 0 #Entramos a la conf del aux port
router(config-line)#loggin sync
```