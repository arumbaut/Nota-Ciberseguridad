- Tags: #router_upgrade

```cisco

RouterPrimario#show version #Muestra el OS que corre actualmente 
RouterPrimario(config-if)#show flash #Mostrar la capacidad de la flash para ver si podemos copiarle el fichero con la actualizacion desde nuestro serv TFTP

De no contar con suficiente espacio borramos lo que esta en la flash siempre haciendo una salva prmero del archivo
RouterPrimario(config)#delet flash:/nombre_fichero

```

![[Pasted image 20260406152747.png|955]]

![[Pasted image 20260406153112.png]]

![[Pasted image 20260406153550.png]]

A continuacion copiamos el fichero con la ios para el router mediante TFTP

```cisco

RouterPrimario#copy tftp flash
```

![[Pasted image 20260406154118.png]]
![[Pasted image 20260406154137.png]]

Verificamos el fichero que copiamos recientemente
```cisco

RouterPrimario#config t
RouterPrimario(config)#boot system flash:/nombre_file.bin
RouterPrimario(config)#exit
RouterPrimario#copy run start
RouterPrimario#reload

Verificamos que se actualizo el SO
RouterPrimario#show version
```

![[Pasted image 20260406154659.png]]


```cisco
Para copiar la nueva configuracion del tftp al router

Router#copy tftp: flash:

Address or name of remote host []? 192.168.1.10         #Ip Serv TFTP

Source filename []? c2900-universalk9-mz.SPA.155-3.M4a.bin  #Archivo IOS new

Destination filename [c2900-universalk9-mz.SPA.155-3.M4a.bin]?  #Confirmar


#Le decimos que no botee de la img anterior
Router(config)#no boot system flash c2900-universalk9-mz.SPA.151-1.M4.bin

#Le decimos que botee de la nueva img
Router(config)#boot system flash c2900-universalk9-mz.SPA.155-3.M4a.bin

#Comprobamos que va a botear de la nueva img
  
Router#show running-config | include boot
boot system flash c2900-universalk9-mz.SPA.155-3.M4a.bin

#Salvamos en memoria
Router#write memory

#Recargamos el router
Router#reload

#verificamos la version
Router#show version

Cisco IOS Software, C2900 Software (C2900-UNIVERSALK9-M), Version 15.5(3)M4a, RELEASE SOFTWARE (fc1)
```