## 1. Chunking: 3 grandes bloques

|**Bloque**|**Tipos de inyección SQL**|
|---|---|
|**I. In-band (canal único)**|Error-based, System Stored Procedure, Illegal/Logically Incorrect Query, UNION, Tautology, End-of-Line Comment, In-line Comment, Piggybacked Query|
|**II. Blind/Inferential (ciega)**|Boolean-based, Time-based (WAITFOR), Heavy Query|
|**III. Out-of-Band (fuera de banda)**|Canal secundario (DNS, HTTP)|

---

## 2. Resumen y **puntos clave** por bloque

### Bloque I: In-band SQL Injection

- **Mismo canal para atacar y extraer**
    
- **Error-based**: provoca errores para leer información directamente.
    
- **System Stored Procedure**: ejecuta SP maliciosos (p.ej. `anyusername or 1=1’`).
    
- **Illegal/Logically Incorrect Query**: inyecta consultas sintácticamente incorrectas para forzar mensajes de error.
    
- **UNION**: añade `UNION SELECT` para combinar resultados legítimos con datos sensibles.
    
- **Tautology**: `… WHERE x OR ‘1’=‘1’` → siempre true, esquiva autenticación.
    
- **End-of-Line Comment**: usa `--` para truncar la consulta legítima.
    
- **In-line Comment**: `/* … */` para ofuscar y evadir filtros.
    
- **Piggybacked Query**: encadena `; DROP TABLE…` para ejecutar múltiples consultas.
    
### Bloque II: Blind/Inferential

- **No hay errores visibles**: el atacante infiere por comportamiento.
    
- **Boolean-based**: envía condiciones que devuelven true/false (`AND 1=2` vs `AND 1=1`).
    
- **Time-based**: usa `WAITFOR` para medir retardos y extraer datos.
    
- **Heavy Query**: consultas muy costosas (`JOIN` múltiples tablas del sistema) para medir tiempo de respuesta.
    

### Bloque III: Out-of-Band

- **Canal secundario** distinto (SMTP, DNS, HTTP UTL_HTTP/`xp_dirtree`).
    
- **Requiere**: habilidad para hacer que el servidor de BD llame a un recurso externo controlado por el atacante.
    

---
## 3. Técnica de Loci + mnemotecnia

Imagina un **castillo de 3 alas**:

- **Ala Este (In-band)**: una gran **tubería** por donde fluyen los 8 tipos de inyección; cada tubería tiene un cartel con su nombre y un color distintivo:
    
    1. Error-based → placa rota que chisporrotea (errores).
        
    2. Stored Proc → armario con tomos de SP.
        
    3. Illegal Query → lápidas mal escritas.
        
    4. UNION → dos ríos que se unen.
        
    5. Tautology → espejo mágico que siempre dice “cierto”.
        
    6. End-Line Comment → línea de metro que se detiene en “–”.
        
    7. In-line Comment → gusano que recorre `/*…*/`.
        
    8. Piggybacked → un tren con dos vagones (consulta + ataque).
        
- **Ala Oeste (Blind/Inferential)**: un tribunal con tres pruebas:
    
    1. Juicio de Verdad/Falsedad (Boolean).
        
    2. Reloj de arena gigante (Time-based WAITFOR).
        
    3. Carretón cargado de pesadas rocas (Heavy Query).
        
- **Ala Norte (Out-of-Band)**: un torreón con una antena parabólica que envía señales DNS/HTTP a un satélite del atacante.