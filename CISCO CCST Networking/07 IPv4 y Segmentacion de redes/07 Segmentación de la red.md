
### Dominios de difusión y segmentación

Dominios de difusión de segmentos de router
En una LAN Ethernet, los dispositivos utilizan difusiones y el Protocolo de resolución de direcciones (Address Resolution Protocol - ARP) para localizar otros dispositivos. ARP envía transmisiones de capa 2 a una dirección IPv4 conocida en la red local para descubrir la dirección MAC asociada. Los dispositivos de LAN Ethernet también localizan otros dispositivos que utilizan servicios. Un host normalmente adquiere su configuración de dirección IPv4 utilizando el Protocolo de configuración dinámica de host (DHCP) que envía transmisiones en la red local para localizar un servidor DHCP.

Los switches propagan las difusiones por todas las interfaces, salvo por aquella en la cual se recibieron. Por ejemplo, si un switch de la ilustración recibiera una difusión, la reenviaría a los demás switches y a otros usuarios conectados en la red.

*Los routers no propagan difusiones. Cuando un router recibe una difusión, no la reenvía por otras interfaces. Por ejemplo, cuando el R1 recibe una difusión en la interfaz Gigabit Ethernet 0/0, no la reenvía por otra interfaz.*

Por lo tanto, cada interfaz de router se conecta a un dominio de transmisión y las transmisiones solo se propagan dentro de ese dominio de transmisión específico.

## Problemas con los dominios de difusión grandes

Un dominio de difusión amplio

Un dominio de difusión grande es una red que conecta muchos hosts. Un problema con un dominio de difusión grande es que estos hosts pueden generar difusiones excesivas y afectar la red de manera negativa. En la figura, LAN 1 conecta a 400 usuarios que podrían generar una cantidad excesiva de tráfico de difusión. Esto da como resultado operaciones de red lentas debido a la cantidad significativa de tráfico que puede causar, y operaciones de dispositivo lentas porque un dispositivo debe aceptar y procesar cada paquete de difusión.

## Comunicación entre redes

La solución es reducir el tamaño de la red para crear dominios de difusión más pequeños mediante un proceso que se denomina *división en subredes*. Estos espacios de red más pequeños se denominan subredes.

En la figura, los 400 usuarios en LAN 1 con la dirección de red 172.16.0.0 / 16 se han dividido en dos subredes de 200 usuarios cada una: 172.16.0.0 / 24 y 172.16.1.0 / 24. Las difusiones solo se propagan dentro de los dominios de difusión más pequeños. Por lo tanto, una transmisión en LAN 1 no se propagaría a LAN 2.

## Razones para la segmentación de redes

La división en subredes disminuye el tráfico de red general y mejora su rendimiento. A su vez, le permite a un administrador implementar políticas de seguridad, por ejemplo, qué subredes están habilitadas para comunicarse entre sí y cuáles no lo están. Otra razón es que reduce el número de dispositivos afectados por el tráfico de difusión anormal debido a configuraciones incorrectas, problemas de hardware o software o intenciones malintencionadas.

Existen diversas maneras de usar las subredes para contribuir a administrar los dispositivos de red.

**Cómo los administradores de red pueden agrupar dispositivos y servicios en subredes**.

![822](../../../attachments/Pasted%20image%2020260321083449.png)

![839](../../../attachments/Pasted%20image%2020260321083550.png)

![755](../../../attachments/Pasted%20image%2020260321083630.png)