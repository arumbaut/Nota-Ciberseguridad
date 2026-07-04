- Tags : #rutas_estaticas_redundantes

### Infraestructura de Red , conexión entre los Routers por Serial Links

Las conexiones Serial Links son típicamente utilizadas en las  T1 Conections y aunque es una tecnología antigua aun podemos encontrarlas en algunos entornos industriales, PP , Frame Relay 

![[Pasted image 20260423101818.png|792]]

En este tipo de infraestructura nos ocurre que tenemos 2 rutas las cuales podemos tomar para llegar a un mismo destino y en un intento del router por balancear  la carga enviara paquetes por una u otra haciendo la red impredecible, ademas que los paquetes llegarían al router de destino desordenados debido a que un camino es mas largo que otro causando problemas al protocolo *TCP*  por lo que entra en juego la **distancia administrativa**   que no es mas que la prioridad que tiene un *Router*  sobre otro.

Por defecto las distancias administrativas de los rutas conectadas directamente es de 0, y por defecto las *rutas estáticas*  del router tienen una distancia administrativa de 1.  Esto quiere decir que *una ruta directamente conectada es mas confiable que una ruta estática*

*La distancia administrativa de las rutas estática las podemos ajustar a nuestra conveniencia.*

Ejemplo de distancias administrativas

![[Pasted image 20260423103900.png|841]]

La numeracion de las interfaces **Serial** nos dicen que: 
Ej S 0/2/0 
1er 0 Hace referencia al Dispositivo por lo que siempre sera 0
2do 0 Hace referencia al Modulo donde se encuentra conectado, en este caso el modulo 2
3ro 0 hace referencia a la interface conectada en el modulo. Hay modulo de 2 ,de tres etc.

#rutas #tabla_rutas_distancia_igual
*Cuando tenemos varias rutas agregada a la misma red solo se refleja en la tabla de rutas la que menor distancia tengan . Si las rutas tienen la misma distancia pues se reflejan las 2*

Configuramos las 2 rutas que tenemos para llegar al las diferentes subredes desde el router B, le agregamos un valor al final de las rutas a aquellas que les modificamos la distancia administrativa para dar preferencia a una ruta sobre otra así en todos los routers con mas de una via de llegara al objetivo 

```cisco
RouterB>enable
RouterB#configure terminal
RouterB(config)#ip route 192.168.0.0 255.255.255.0 10.0.0.1
RouterB(config)#ip route 192.168.0.0 255.255.255.0 10.0.0.10 10

RouterB(config)#ip route 192.168.20.0 255.255.255.0 10.0.0.10
RouterB(config)#ip route 192.168.20.0 255.255.255.0 10.0.0.1 10


```