Una vez que los routers son vecinos (gracias al protocolo Hello), el siguiente paso es compartir qué redes tienen conectadas.

- **LSA (Link State Advertisement):** Es un anuncio individual que crea el router para **cada una** de sus redes directamente conectadas. Contiene datos como la dirección de red y la máscara.
    
- **LSU (Link State Update):** Es el "paquete de envío". El router agrupa varios LSAs y los envía a sus vecinos en una actualización de estado de enlace.
    
- **LSDB (Link State Database):** Es la base de datos donde el router guarda todos los LSAs recibidos de sus vecinos. Al final, todos los routers en la misma área tendrán una LSDB idéntica, lo que significa que todos tienen el mismo "mapa" de la red.
    

### 2. El Algoritmo SPF (Dijkstra)

Tener el mapa (LSDB) no es suficiente; el router necesita saber cuál es el camino más corto hacia cada destino.

- **Algoritmo SPF:** También conocido como **Algoritmo de Dijkstra**. Es el motor matemático que procesa la información de la LSDB.
    
- **Funcionamiento:** El algoritmo analiza cada red en la base de datos, calcula el **costo** para llegar a ellas y determina cuál es el **siguiente salto** (next hop) más eficiente.
    
- **Resultado Final:** La salida de este algoritmo es lo que finalmente llena la **Tabla de Rutas** del router.
    
#### Importante todos  los routers vecinos hacen el mismo procedimiento.
### 3. Ejemplo Práctico tratado en clase

La clase utiliza un escenario con el **Router A** y el **Router B**:

- **Configuración del Router A:** Tiene conectadas las redes `10.0.0.0/24` y `172.16.0.0/30`.
    
- **Acción:** El Router A genera un LSA para cada una y las envía al Router B en un LSU.
    
- **Respuesta:** El Router B recibe el LSU, extrae los LSAs y los guarda en su propia LSDB. Luego, el Router B hace lo mismo con sus propias redes para informar al Router A.
    
- **Cálculo:** Ambos routers ejecutan el algoritmo SPF sobre sus bases de datos actualizadas para ver cómo llegar a las redes del otro.
    

### Resumen del proceso para tus notas:

1. **Protocolo Hello:** Establece la relación de vecindad.
    
2. **LSU/LSA:** Se intercambian los anuncios de las redes conectadas.
    
3. **LSDB:** Se construye el mapa completo de la red en cada router.
    
4. **Algoritmo SPF (Dijkstra):** Se calcula el camino más corto basándose en el costo.
    
5. **Tabla de Rutas:** Se añaden las mejores rutas calculadas para empezar a mover tráfico.

![[Pasted image 20260424120028.png|701]]

![[Pasted image 20260424121729.png]]

![[Pasted image 20260424121756.png]]

![[Pasted image 20260424121956.png]]

![[Pasted image 20260424122138.png]]


## Una vez actualizadas las LSDB se calcula la tabla de rutas mediante Algoritmo SPF o Dykstras Algotithm y este genera las Tablas de Rutas

![[Pasted image 20260424122252.png]]


# Resumen de terminologías 

![[Pasted image 20260424122715.png|692]]

![[Pasted image 20260424122909.png|693]]

![[Pasted image 20260424123003.png|693]]