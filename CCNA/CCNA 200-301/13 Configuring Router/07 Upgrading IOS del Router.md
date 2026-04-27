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
RouterPrimario(config)#boot sysem flash:/nombre_file.bin
RouterPrimario(config)#exit
RouterPrimario#copy run start
RouterPrimario#reload

Verificamos que se actualizo el SO
RouterPrimario#show version
```

![[Pasted image 20260406154659.png]]