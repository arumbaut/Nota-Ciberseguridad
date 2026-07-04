
*DTP* es un protocolo propietario de *CISCO* que permite conectar 2 SW .
El protocolo DTP esta activo pot defecto. Si el SW 2 tine un puerto configurado con DTP con cero configuración y le conectamos otro sw en este caso SW 1 y tiene el puerto configurado en modo Trunk , automáticamente crea un enlace Trunkal y agrega todas las VLANs a este . **Esto es extremadamente peligroso.**

A continuacion las combinaciones del modo de los puertos que pueden generar un enlace trunkal

![[Pasted image 20260410093109.png|616]]

##### La configuracion de DTP tine dos estados 
1 - Dynamic - Auto (Dispositivos modernos)
2 - Dynamic - Desirable (Versiones 2950 o anteriores establecido por defecto)


#### Configuracion Estática de los puertos del SW
1 - Acces
1 - Trunk

### Casos de Estados

![[Pasted image 20260410094445.png|736]]

![[Pasted image 20260410094533.png|746]]

![[Pasted image 20260410094653.png|746]]

![[Pasted image 20260410094745.png|750]]

![[Pasted image 20260410094829.png|749]]

![[Pasted image 20260410095002.png|866]]

### Mostrar Configuración del protocolo DTP

```cisco
sw#show int trunk
sw#show dtp int f0/24
```

![[Pasted image 20260410095414.png|755]]

### Cambiar comportamiento del comportamiento de DTP [Auto o  Desarible]
```cisco
sw(config)#interface f0/24
sw(config)#switchport mode dynamic desirable
```

![[Pasted image 20260410101007.png|804]]

### Evitar este comportamiento. Apagar DTP

```cisco
sw(config)#interface range f0/1 - 24 , g0/1 - 2
sw(config-if0range)#switchport mode access
sw(config-if0range)#switchport access v1
sw(config-if0range)#switchport nonegotiate
```


