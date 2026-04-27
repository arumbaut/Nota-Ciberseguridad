Existen ciertas direcciones, como la dirección de red y la dirección de difusión, que no se pueden asignar a los hosts. También hay direcciones especiales que pueden asignarse a los hosts, pero con restricciones respecto de la forma en que dichos hosts pueden interactuar dentro de la red.

**Direcciones de loopback**

Las direcciones de bucle invertido (loopback) (127.0.0.0 /8 o 127.0.0.1 a 127.255.255.254) se identifican más comúnmente como solo 127.0.0.1. Estas son direcciones especiales utilizadas por un host para dirigir el tráfico hacia sí mismo. Por ejemplo, el comando **ping** se usa comúnmente para probar conexiones a otros hosts. Pero también puede usar el comando **ping** para probar si la configuración de IP en su propio dispositivo, como se muestra en la figura.

**Direcciones de enlace local**

Direcciones link-local o direcciones IP privadas automáticas (APIPA) 169.254.0.0/16o 169.254.0.1 a 169.254.255.254 Los utiliza un cliente de Windows para autoconfigurarse en caso de que el cliente no pueda obtener un direccionamiento IP a través de otros métodos. Las direcciones locales de vínculo se pueden utilizar en una conexión de punto a punto, pero no se utilizan comúnmente para este propósito.