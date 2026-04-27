
### Trama de Ethernet
![](../../../attachments/Pasted%20image%2020260321054833.png)


Los números debajo, son el número de bytes para cada uno de estos campos. Si desea traducir esto a bits, simplemente multiplique cada uno de estos números por ocho y le dará la cantidad de bits.

El primer campo es el preámbulo. Esto se utiliza para obtener la tarjeta NIC, la NIC de recepción, en sincronización con los bits que bajan por el cable.

El delimitador de trama de inicio, esto indica a la tarjeta de interfaz de red receptora que, tras este delimitador de trama inicial, será la información real asociada con la trama Ethernet.

Dirección MAC de destino. La dirección MAC de destino es la direccion MAC de destino en esa red. Esa es la dirección MAC de la tarjeta NIC a dónde va esta trama de Ethernet en esta red.

La dirección MAC de origen, esta es la dirección MAC del dispositivo que originó esta trama de Ethernet, la dirección MAC de la tarjeta de interfaz de red, la NIC de Ethernet, que originó esta trama de Ethernet.

La longitud, o tipo de campo. Este campo puede ser una de dos cosas:
  Podría ser la longitud, y esa sería la longitud de los datos, lo que a veces llamamos carga útil, cuántos bytes hay en la porción de datos de esta trama de Ethernet; o puede ser un tipo de campo que dice qué tipo de datos son, es un paquete IPv4, o es un paquete IPv6.

Lo siguiente son los datos encapsulados reales. Esto podría ser un paquete de IPv4, podría ser un paquete de IPv6 y, luego, con el paquete IPv4, digamos, podría haber otros protocolos también.  Estos son todos los datos, este podría ser el paquete IPv4, con el encabezado TCP, o junto con el encabezado HTTP, o cualquier información que se haya encapsulado.

Por último, tenemos lo que se conoce como secuencia de verificación de tramas (FCS) Esto lo utiliza el dispositivo receptor para hacer alguna verificación de errores, asi asegurarnos que no hubo errores durante la transmisión.


### Paquete IPv6

![](../../../attachments/Pasted%20image%2020260321054230.png)