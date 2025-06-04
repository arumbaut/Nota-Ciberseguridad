![](../../../attachments/image20250602221258.png)

**Versión**

· Este campo contiene un valor binario de 4 bits establecido en "0110" que lo identifica como un paquete IPv6.

**Clase de tráfico**

· Este campo de 8 bits es equivalente al campo Differentiated Services (DS) de IPv4

Etiqueta de flujo

· Este campo de 20 bits sugiere que todos los paquetes con la misma etiqueta de flujo sean manejados de la misma manera por los routers

Longitud de la payload(carga útil)

· Este campo de 16 bits indica la longitud de la porción de datos o de la payload (carga útil) del paquete IPv6.

**Próximo encabezado**

· Este campo de 8 bits es equivalente al campo "Protocolo" de IPv4.

· Es un valor que indica el tipo de payload (carga útil) de datos que contiene el paquete, lo cual permite que la capa de red transmita los datos al protocolo de capa superior apropiado.

**Límite de saltos**

· Este campo de 8 bits sustituye el campo TTL de IPv4.

· Cada router que reenvía el paquete reduce este valor en 1.

· Cuando llega a cero, se descarta el paquete y se envía un mensaje de tiempo superado de ICMPv6 al host de origen que indica que el paquete no llegó a destino porque excedió el límite de saltos.

**Dirección IPv6 de origen**

· Este campo de 128 bits identifica la dirección IPv6 de origen del host emisor.

**Dirección IPv6 de destino**

· Este campo de 128 bits identifica la dirección IPv6 del host receptor.