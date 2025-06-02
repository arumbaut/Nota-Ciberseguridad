![](../../../attachments/image20250602221131.png)

**Versión**

· Contiene un valor binario de 4 bits establecido en "0100" que lo identifica como un paquete de IPv4.

**Longitud del encabezado de Internet**

· Un campo de 4 bits que contiene la longitud del encabezado IP.

· La longitud mínima de un encabezado IP es de 20 bytes.

**Servicios diferenciados o DiffServ (DS)**

· Antiguamente conocido como el campo de "Tipo de Servicio" (ToS, siglas en inglés), el campo DS es un campo de 8 bits utilizado para determinar la prioridad de cada paquete.

· Los seis bits más importantes del campo DiffServ se encuentran en el punto de código de servicios diferenciados (DSCP, Differentiated Services Code Point).

· Los dos últimos bits son los bits de notificación de congestión explícita (ECN, Explicit Congestion Notification).

**Longitud total**

· Especifica la longitud total del paquete IP incluyendo el encabezado IP y los datos del usuario.

· El campo de longitud total es de 2 bytes, por lo que el tamaño máximo de un paquete IP es de 65 535 bytes.

**Identificación, Banderas y Desplazamiento de fragmentos.**

· A medida que un paquete IP se moviliza, es posible que deba cruzar una ruta que no es capaz de manejar el tamaño total del paquete.

· El paquete se dividirá fragmentará en paquetes más pequeños y se rearmará más adelante.

· Estos campos se utilizan para fragmentar y rearmar los paquetes.

**Tiempo de Existencia (TTL, siglas en inglés)**

· Contiene un valor binario de 8 bits que es utilizado para delimitar el tiempo de existencia de un paquete

· El emisor del paquete establece el valor inicial de TTL que se reduce en uno cada vez que un router procesa el paquete.

· Si el campo TTL llega a cero, el router descarta el paquete y envía a la dirección IP de origen un mensaje de tiempo superado del protocolo de mensajes de control de Internet (ICMP).

**Protocolo**

· Este campo se utiliza para identificar el protocolo de capa superior.

· Este valor binario de 8 bits indica el tipo de carga de datos que lleva el paquete, lo que permite que la capa de red transmita los datos al protocolo de capa superior apropiado.

· ICMP (1), TCP (6) y UDP (17) son algunos valores comunes.

**Checksum del encabezado**

· Corresponde a un valor que es calculado basándose en el contenido del encabezado IP del paquete.

· Se utiliza para determinar si se han introducido errores durante la transmisión.

**Dirección IPv4 de origen**

· Contiene un valor binario de 32 bits que representa la dirección IPv4 de origen del paquete.

· La dirección IPv4 de origen siempre es una dirección de Unicast.

**Dirección IPv4 de destino**

· Contiene un valor binario de 32 bits que representa la dirección IPv4 de destino del paquete.

**Opciones y Relleno**

· Este es un campo que varia la longitud de 0 a un múltiplo de 32 bits

· Si las opciones de valores no son un múltiplo de 32 bits, se agregan o intercalan ceros para garantizar que este campo contenga un múltiplo de 32 bits