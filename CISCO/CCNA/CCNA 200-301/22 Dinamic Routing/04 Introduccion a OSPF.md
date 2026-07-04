
- Tags : #ospf 

*OSPF*  proceso de descubrimiento de vecinos *(Discover Neighbors)*. Se utiliza el *HELLO PROTOCOL*  para intercambiar información entre los routers para que esto puedan conformar la relación entre vecinos. Los routers se estarán enviando periódicamente *HELLO MESSAGES*  que contiene información de estos para agregar a su tabla para establecer una proximidad o una relación de vecino


Esta tabla es fundamental para entender cómo **OSPF** establece una relación de vecindad. En OSPF, para que dos routers se conviertan en "vecinos" y compartan sus tablas de rutas, **ciertos valores en el paquete Hello deben coincidir exactamente**. Si uno falla, la vecindad no se forma.

![[Pasted image 20260424084227.png|699]]

![[Pasted image 20260424084613.png|692]]

### 1. Subnet/Mask (Subred y Máscara)

- **De qué se encarga:** Verifica que ambos routers estén en la misma red física.    
- **Uso:** En redes multiacceso (como Ethernet), los routers deben tener la misma máscara de subred en las interfaces conectadas. Si el Router A es `/24` y el Router B es `/30`, nunca formarán vecindad.    

### 2. Hello Interval (Intervalo de Hola)

- **De qué se encarga:** Define cada cuántos segundos el router envía un paquete Hello para decir "sigo vivo".    
- **Uso:** Por defecto suele ser 10 segundos en redes Ethernet. **Deben coincidir en ambos routers.** Si el Router A envía cada 10s y el Router B espera cada 30s, habrá un error.
### 3. Dead Interval (Intervalo de Muerte)

- **De qué se encarga:** Es el tiempo de espera antes de declarar a un vecino como "caído".    
- **Uso:** Normalmente es **4 veces el Hello Interval** (si el Hello es 10s, el Dead es 40s). Si el router no recibe un Hello del vecino en este tiempo, borra todas las rutas que aprendió de él. **También debe coincidir en ambos routers.**  

### 4. Area ID (ID de Área)

- **De qué se encarga:** Segmentar la red para que sea más eficiente.    
- **Uso:** OSPF utiliza áreas (como la Área 0, que es el _backbone_). Para que dos routers sean vecinos, sus interfaces conectadas **deben pertenecer a la misma área**.   

### 5. Authentication (Autenticación)

- **De qué se encarga:** Seguridad.    
- **Uso:** Es opcional (`opt`). Si configuras una contraseña en el Router A, el Router B debe tener la **misma contraseña y el mismo tipo** (texto plano o MD5) para poder hablar entre ellos.   

### 6. Stub Area Flag (Bandera de Área Stub)

- **De qué se encarga:** Identifica si el área es "especial" (Stub).    
- **Uso:** Una "Stub Area" es una zona que no recibe rutas externas para ahorrar memoria. Ambos routers deben estar de acuerdo en si el área es Stub o no; si hay desacuerdo, no hay vecindad.   

### 7. MTU Size (Tamaño de la Unidad Máxima de Transmisión)

- **De qué se encarga:** Define el tamaño máximo del paquete que puede pasar por la interfaz.    
- **Uso:** Aunque técnicamente no impide que se vean (estado _ExStart/Exchange_), si las MTU no coinciden, los routers se quedarán "atascados" y no podrán intercambiar sus bases de datos de rutas.