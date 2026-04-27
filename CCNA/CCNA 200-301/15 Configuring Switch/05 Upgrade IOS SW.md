- Tags: #switch_upgrade

```cisco
switch1>enable
switch1#show version
```

![[Pasted image 20260407111243.png]]

![[Pasted image 20260407111335.png]]Los ficheros de SO son .bin

Vemos lo que hay en ese directorio
![[Pasted image 20260407111456.png]]
Cargamos desde un servidor TFTP el fichero .bin con la nueva actualización del SO
Antes siempre verificar que tenemos el espacio suficiente para copiar la actualización
![[Pasted image 20260407111750.png]]

![[Pasted image 20260407112042.png]]

Verificamos que se copio 

![[Pasted image 20260407112224.png]]

Verificamos la integridad del archivo atendiendo a su hash comparandolo con el que obtenemos de cisco al descargar el .bin
![[Pasted image 20260407112808.png]]



![[Pasted image 20260407112504.png]]

Revisamos la version con show version