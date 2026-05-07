

Esto es un dispositivo que nos permite controlar los APs de nuestra red evitándonos tener que calcular los canales y las frecuencia para que no se solapen las comunicaciones.

WLC: Wireless Lan Control System 
*Son capaces de manejar hasta 6000 Access Point* depende del equipo todo desde una misma interface.

Si el *WLC por algún motivo se pone offline* , debido a una actualización o que cogió candela, *pues perderemos el  acceso a todos los APs conectados a ese controlador, como consecuencia todo el sistema quedara offline*. Esto es un problema cuando utilizamos infraestructura de Red Inálambrica. *Aunque podemos resolver este problema agregando redundancia a nuestra red agregando un WLC secundario incluso 3.*

Cada uno de estos *WLC puede manejar 64000 redes clientes*

![[Pasted image 20260504112058.png|717]]

![[Pasted image 20260504112116.png|721]]

![[Pasted image 20260504112141.png|723]]

Para agregar mas nivel de redundancia agregaremos redundancia de Hardware

![[Pasted image 20260504112316.png|727]]


![[Pasted image 20260504112601.png|739]]

Para brindar soporte a nuestra red inalámbrica también utilizaremos otros dispositivos como:

**MSE** : Mobility Services Engine. La nueva version de este equipo se llama Cisco Mobility Experience CMX. Este equipo nos permite localizar con bastante precision donde esta cualquier dispositivo en la red , utiliza triangulación para saber donde esta el adaptador de red

**Cisco DNA Center** : Este equipo nos permite monitorear todos los dispositivos en la red, wireless , switches, routers, nos permite ademas monitorear su rendimiento

Cisco Wireless Network también permite ver un mapa de calor  atraves de los WLC

![[Pasted image 20260504113842.png|784]]


Hay una opción que no requiere tener todo este hardware en nuestra empresa y es tener un Cloud Base Controller. Lo que hará es conectarse a los servicios de cisco y desde alli administraremos toda la infraestructura de APs.  Esto se hace con Cisco Meraki Wireless System