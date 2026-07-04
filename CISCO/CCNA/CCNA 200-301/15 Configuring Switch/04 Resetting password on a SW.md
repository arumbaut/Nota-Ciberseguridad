
Reseteamos el pass del enable mode. el pass esta guardado en un fichero llamado config.text en la flash. 

Debemos acceder al este fichero mediante la ROMmon mode

Con el cable de consola conectado desconectamos el cable de energia 
Presionamos el boton de al frente del switch y conectamos el cable de corriente y mantenemos presionado el boton mientras esta iniciando el sw

![[Pasted image 20260407105428.png|716]]

![[Pasted image 20260407105447.png]]

![[Pasted image 20260407105507.png]]


Una vez dentro podemos borrar el fichero si no necesitamos las configuraciones sino podemos renoombrarlo 
```cisco
switch:delet flash:config.text
```

Pero lo que vamos a hacer es un backup
![[Pasted image 20260407105746.png]]

![[Pasted image 20260407105816.png]]

Hecho esto reiniciamos el switch
```cisco
switch:boot
```

![[Pasted image 20260407110003.png]]

Ya nos permite entrar en el modo de configuración pero no tiene nada de las configuraciones previas.

Y vemos lo que tenemos en la flash
![[Pasted image 20260407110145.png]]

Renombramos el fichero de backup como original y cambiamos la password ya que estamos dentro 
![[Pasted image 20260407110341.png]]

Copiamos la startup-config a la running-config
```cisco
switch#copy flash:/config.text running-config
switch1#configure terminal

Teniendo la configuracion ya cargada entramos al modo config y establecemos un pass nuevo
switch(config)#enable secret cisco
switch#copy running-config startup-config

```