- Tags: #rip_conf

```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#router rip
RouterA(config-router)#version 2  
RouterA(config-router)#no aute-summary

Le decimos al router que rutas anunciar y solo puede anunciar rutas conectadas directamente
RouterA(config-router)#network 10.0.0.0
RouterA(config-router)#network 192.168.0.0


RouterA#show ip protocols
```

```cisco
RouterB>enable
RouterB#configure terminal
RouterB(config)#router rip
RouterB(config-router)#version 2  
RouterB(config-router)#no aute-summary
RouterB(config-router)#network 10.0.0.0
RouterB(config-router)#network 192.168.10.0


RouterB#show ip protocols
```

```cisco
RouterC>enable
RouterC#configure terminal
RouterC(config)#router rip
RouterCconfig-router)#version 2  
RouterC(config-router)#no aute-summary
RouterC(config-router)#network 10.0.0.0
RouterC(config-router)#network 192.168.20.0


RouterC#show ip protocols

```

El protocolo **RIP** (Routing Information Protocol) es uno de los protocolos de enrutamiento más antiguos y sencillos que existen. Se clasifica como un protocolo de **Vector de Distancia**.

Para entender cómo funciona, imagina que el router no conoce el mapa completo de la ciudad (la red), sino que solo le pregunta a sus vecinos qué destinos conocen y a qué distancia están.

---
### 1. El concepto de "Métrica": Los Saltos

A diferencia de OSPF (que usa el ancho de banda), RIP solo se fija en el **conteo de saltos** (hop count).

- Cada router que un paquete debe atravesar para llegar a su destino cuenta como **1 salto**.    
- **El límite es 15 saltos:** Si un destino está a 16 saltos, RIP lo considera "inalcanzable" y descarta el paquete. Por eso no sirve para redes muy grandes.
    
### 2. ¿Cómo se comunican los routers?

RIP funciona mediante un sistema de "chismes" o actualizaciones periódicas:

- **Actualizaciones cada 30 segundos:** Por defecto, cada router envía su tabla de rutas completa a todos sus vecinos, incluso si no ha habido cambios.    
- **Vector de Distancia:** Envía la dirección de red (el vector) y la distancia (saltos).
    
---
### 3. El proceso de aprendizaje

1. **Al inicio:** Un router solo conoce sus redes directamente conectadas (salto 0).    
2. **Intercambio:** El Router A le dice al Router B: _"Yo puedo llegar a la red 192.168.0.0"_.  
3. **Actualización:** El Router B recibe esa info, le suma 1 al contador de saltos y anota en su tabla: _"Para ir a 192.168.0.0, debo enviárselo al Router A (distancia: 1 salto)"_.    

---

### 4. Versiones de RIP

Existen tres variantes principales:

|**Característica**|**RIPv1**|**RIPv2**|**RIPng**|
|---|---|---|---|
|**Tipo**|Classful (No admite VLSM)|Classless (Admite VLSM/Subredes)|Para IPv6|
|**Envío**|Broadcast (255.255.255.255)|Multicast (224.0.0.9)|Multicast (FF02::9)|
|**Seguridad**|Sin autenticación|Admite contraseñas|IPsec|

---
### 5. Mecanismos para evitar bucles

Como RIP tarda en reaccionar a los cambios (convergencia lenta), usa técnicas para no crear bucles infinitos:

- **Split Horizon (Horizonte Dividido):** Un router nunca envía información de una ruta de vuelta por la misma interfaz por la que la aprendió.    
- **Route Poisoning (Envenenamiento de ruta):** Cuando una red cae, el router le pone inmediatamente una métrica de **16** para avisar a todos que ya no es válida.    
- **Hold-down Timers:** El router espera un tiempo antes de creerse una nueva ruta hacia un destino que acaba de fallar, evitando cambios constantes ("flapping").    

---
### ¿Cómo se configura (RIPv2)?

Si quisieras cambiar tu arquitectura de OSPF a RIP, el comando sería:

```cisco
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 10.0.0.0
Router(config-router)# network 192.168.10.0
Router(config-router)# no auto-summary  (Para que no agrupe las redes automáticamente)
```

**Dato curioso:** RIP tiene una **Distancia Administrativa de 120**. Esto significa que si un router aprende una ruta por OSPF (DA 110) y por RIP (DA 120), siempre le creerá más a OSPF porque su número es menor.