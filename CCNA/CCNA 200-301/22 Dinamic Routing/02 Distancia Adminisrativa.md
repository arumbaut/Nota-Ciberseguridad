![[Pasted image 20260423221615.png|622]]

Si tenemos multiples protocolos de enrutamiento corriendo en nuestra red, el router agregará rutas a la tabla de rutas basado en la distancia administrativa del router.
Si tenemos EIGRP OSPF IS-IS RIP todos corriendo al mismo tiempo el único router que sera agregado a la tabl de rutas sera el EIGRP Routes 

### 1. ¿Qué es la Distancia Administrativa?

Imagina que la Distancia Administrativa es el "índice de confiabilidad" de un protocolo. El router es como un jefe que recibe consejos de diferentes asesores (protocolos). Si dos asesores le dicen cómo llegar al mismo sitio, el jefe creerá al que tenga el número de AD **más bajo**.

### 2. La jerarquía de los protocolos (Valores por defecto de Cisco)

Para que entiendas por qué **EIGRP** gana en tu ejemplo, mira los valores estándar:

- **Rutas Conectadas directamente:** 0    
- **Rutas Estáticas:** 1    
- **EIGRP (Interno):** **90**   
- **OSPF:** 110    
- **IS-IS:** 115    
- **RIP:** 120
    

### 3. ¿Por qué ganaría EIGRP?

Si tienes corriendo EIGRP, OSPF, IS-IS y RIP al mismo tiempo, y todos ellos descubren una ruta hacia la red `10.1.1.0/24`:

1. El router mira sus opciones.    
2. Ve que EIGRP ofrece una ruta con **AD 90**.    
3. Ve que OSPF ofrece la misma ruta con **AD 110**, IS-IS con **115** y RIP con **120**.    
4. Como **90 es el número más bajo**, el router considera que EIGRP es el más confiable.    
5. **Resultado:** Solo la ruta de *EIGRP* se instala en la Tabla de Rutas (Routing Table).

### 1. El Router tiene varias "bases de datos"

Imagina que el router tiene varias libretas de notas, una por cada protocolo:

- **Libreta EIGRP:** Tiene sus propias rutas y vecinos.    
- **Libreta OSPF:** Tiene su propio mapa de la red.    
- **Libreta RIP:** Tiene su lista de saltos.
    
Cada protocolo funciona de forma independiente. Los routers vecinos que solo hablan OSPF **nunca verán** las rutas de *EIGRP* a menos que tú hagas un proceso llamado **Redistribución** (que es como traducir de un idioma a otro).


![[Pasted image 20260423223040.png|762]]

La métrica es la forma en que se elige la ruta dentro del propio protocolo.
Si tenemos dos router con OSPF en la misma red utilizaremos el Calculo del Bandwidth  para descifrar cuan lejos esta la ruta de destino, entonces la ruta con el bandwidth mas rápido ganara