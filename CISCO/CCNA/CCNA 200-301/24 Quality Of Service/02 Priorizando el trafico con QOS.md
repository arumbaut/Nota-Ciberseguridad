- Tags: #qos_priority

![[Pasted image 20260427125913.png|776]]

### Mecanismos de **encolado (Queuing)** dentro de las políticas de *Calidad de Servicio (QoS)*
### 1. FIFO (First-In, First-Out)

Es el método más básico. "El primero que llega, es el primero que sale".

- **Cómo funciona:** No hay prioridades. Si un paquete de video llega después de una descarga pesada de un archivo, el video tendrá que esperar a que el archivo termine de pasar.    
- **Problema:** Causa mucha latencia y _jitter_ en aplicaciones sensibles como VoIP.---

### 2. WFQ (Weighted Fair Queuing)

Trata de ser "justo" dividiendo el ancho de banda entre los diferentes flujos de datos.

- **Cómo funciona:** Clasifica el tráfico automáticamente (por ejemplo, separa el tráfico web del correo). Los flujos de poco volumen (interactivos) suelen recibir prioridad sobre los de gran volumen (descargas FTP).    
- **Ventaja:** Evita que una sola descarga pesada "mate" la conexión de los demás usuarios.
    
### 3. CBWFQ (Class-Based Weighted Fair Queuing)

Es una evolución de WFQ donde **tú** defines las clases de tráfico.

- **Cómo funciona:** Tú creas "cajones" específicos. Por ejemplo: "Cajón 1 para aplicaciones críticas (20% del ancho de banda)" y "Cajón 2 para tráfico general (10%)".    
- **Ventaja:** Garantiza un ancho de banda mínimo para cada clase de tráfico que consideres importante.
    
### 4. LLQ (Low Latency Queuing)

Es **CBWFQ más una "Vía de Emergencia"**. Es el estándar de oro para VoIP.

- **Cómo funciona:** Es idéntico al *CBWFQ*, pero incluye una **Priority Queue (PQ)**. Todo lo que pongas en esa cola de prioridad (como la voz) se procesa **antes** que cualquier otra clase, sin importar qué tan llena esté la red.    
- **Uso ideal:** Se usa exclusivamente para voz y video en tiempo real.
    

---

### Resumen Comparativo

|**Mecanismo**|**¿Prioriza Voz?**|**Complejidad**|**Uso Recomendado**|
|---|---|---|---|
|**FIFO**|No|Muy Baja|Enlaces muy rápidos donde no hay congestión.|
|**WFQ**|Un poco|Media|Redes estándar sin configuración manual.|
|**CBWFQ**|No garantiza latencia|Alta|Garantizar ancho de banda a datos importantes.|
|**LLQ**|**Sí (Excelente)**|Alta|Redes empresariales con VoIP y Videoconferencia.|