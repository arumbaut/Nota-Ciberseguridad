- Tags: #ipv4 #ipv6


# IPv4
#### *Las direcciones IPv4 tienen 4 octetos lo que representan unos 32 bits de longitud*

![[Pasted image 20260402120813.png|679]]


# IPv6
#### *Las direcciones IPv6 tienen 32 nibles o 32 valores hexadecimales lo que representan unos 128 bits de longitud*

![[Pasted image 20260402121854.png|870]]

![[Pasted image 20260402122248.png|768]]

### Para la red no es obligatorio 64 bits pero es lo que se recomienda y como el protocolo fue diseñado

## Reglas para acortar las direcciones IPv6 

[[01 IPv6#Existen 2 reglas para reducir el numero de dígitos duodecimales en las direcciones IPv6]]

![[Pasted image 20260402123248.png|677]]

![[Pasted image 20260402123553.png|667]]

![[Pasted image 20260402124000.png|631]]

## Tipos de IPv6

![[Pasted image 20260402125058.png|476]]
![[Pasted image 20260402125247.png|498]]

![[Pasted image 20260402125934.png|630]]

## IPv6 Address Adquisition

![[Pasted image 20260402133233.png|708]]


### Windows
![[Pasted image 20260402133253.png|721]]

### LINUX, MAC
#### Divide la direcion MAC en 2

![[Pasted image 20260402133339.png|707]]

#### Rellena el espacio en blanco con lo siguiente
![[Pasted image 20260402133444.png|504]]

#### Tomamos el septimo bit y lo convertimos en el opuesto de su valor actual 

Recordemos que cada valor hexadecimal se representa con 4 bits por lo tanto para acceder al 7 bit es necesario convertir los 2 primeros valores hex a binario y modificar el valor del 7 bit a su opuesto 

![[Pasted image 20260402133617.png|570]]

Dejándonos una direccion de host
![[Pasted image 20260402133952.png|574]]

Y completando la dirección con la porcion de red del router

![[Pasted image 20260402134204.png|627]]


Una vez configurada la dirección IP del host este envía un mensaje de aviso al router
![[Pasted image 20260402134317.png|535]]