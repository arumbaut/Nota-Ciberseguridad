- Tags : #nat 

**NAT**  es un protocolo que nos permite  la modificación de la dirección IP de origen o destino  y la modificación del puerto de origen o destino , a medida que el mensaje atraviesa un router.

*Como norma general un Router no modifica un paquete mas allá de el campo TTL. Para que un router pueda realizar estas modificaciones en la red y el puerto debe ser configurado el NAT en este.*

![[Pasted image 20260428114300.png|734]]

Lo que hacemos es remplazar  nuestra IP privada por la IP publica de salida de nuestro Router, y cuando retorna la respuesta a nuestra petición remplazamos la IP publica por la IP privada de nuestra red.

### Tipos de NAT
![[Pasted image 20260428114917.png|724]]

![[Pasted image 20260428115225.png|645]]