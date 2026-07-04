Esquema del ejercicio

![[Pasted image 20260421125055.png|621]]

Vale destacar que en una mismo interface pueden coexistir la dirección IPv4 y IPv6

```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#interface f0/0
RouterA(config)#ipv6 address 2001:db8:a::1/64 

RouterA#show ipv6 interface brief

#Cambiar la Link Local Address
RouterA(config)#int f0/0
RouterA(config-if)#ipv6 address fe80::1 link-local

```

Una de las ventajas de la *Link Local Address*   es que como esta solo esta diponible en la red de area local podemos asignar esta Link Local Address a cada una de las Interfaces del Router

En IPv4, cada interfaz de un router **debe** tener una dirección IP única; no puedes poner la misma IP en dos patas del router porque el equipo se bloquea y da error de conflicto. Sin embargo, en IPv6 con las direcciones **Link-Local** (las que empiezan por `fe80::`), las reglas cambian.

La clave está en que una dirección Link-Local **solo tiene validez dentro del cable físico (o segmento de red)** al que está conectada la interfaz.

###### ¿Por qué se puede repetir la misma IP en todas las interfaces?

Como el router nunca va a "enrutar" una dirección `fe80::` hacia afuera (los routers no reenvían paquetes Link-Local a otras redes), no hay riesgo de conflicto global.

Para el router, la dirección `fe80::1` en la interfaz _Gigabit0/0_ es un mundo totalmente distinto a la dirección `fe80::1` en la interfaz _Gigabit0/1_. El switch y los dispositivos conectados a cada interfaz solo ven su "mundo" local.

### Ventajas de usar la misma Link-Local (ej. `fe80::1`) en todo el router:

- **Administración simplificada:** En lugar de tener que recordar que la puerta de enlace de la planta 1 es la `fe80::254:a3f2...` y la de la planta 2 es otra distinta, puedes configurar **todas** las interfaces del router como `fe80::1`.
    
- **Configuración fácil para los clientes:** Todos los PCs de la empresa, sin importar en qué departamento o VLAN estén, sabrán que su **Default Gateway** es siempre `fe80::1`.
    
- **Sustitución de hardware:** Si cambias el router por uno nuevo y le pones la misma Link-Local manual, los dispositivos finales no notarán el cambio y seguirán teniendo salida a internet sin actualizar nada.
### Autoconfiguración mediante SLAC

Uno de los puntos clave es el uso de **SLAAC** (Stateless Address Autoconfiguration):

- Al configurar una dirección IPv6 global en el router, este comienza a enviar "anuncios" (Router Advertisements).
    
- La computadora Windows recibe ese anuncio y genera automáticamente su propia dirección IPv6 global sin necesidad de un servidor DHCP.
- **Default Gateway automático:** En IPv6, Windows utiliza automáticamente la dirección _Link-Local_ del router como su puerta de enlace predeterminada, en lugar de la dirección global. 


![[Pasted image 20260421135339.png]]

