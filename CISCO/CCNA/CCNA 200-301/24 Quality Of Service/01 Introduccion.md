- Tags: #qos

QOS se utiliza para priorizar algún tipo de paquetes que viajen por nuestra red y que necesitamos que se manejen de forma principal en nuestros dispositivos con el objetivo de que no exista perdida de datos o un retraso en la comunicación ejemplo la comunicación VoIP

### **Barreras para la implementación de VoIP**

![[Pasted image 20260427125434.png]]

![[Pasted image 20260427125622.png|606]]

### 1. Code Delay (Retraso de Codificación) - **Fijo**

Es el tiempo que tarda el dispositivo (como un teléfono IP) en convertir tu voz analógica en datos digitales usando un software llamado **Codec**.

- **Ejemplo:** El tiempo que le toma al micrófono y al procesador de tu móvil "traducir" tu hola a ceros y unos. 

### 2. Packetization Delay (Retraso de Paquetización) - **Fijo**

Una vez que la voz es digital, hay que cortarla en trozos pequeños y ponerles una etiqueta (encabezado) para que puedan viajar por la red.

- **Ejemplo:** Es como el tiempo que tardas en meter cartas en sobres antes de enviarlas al correo.
    
### 3. Queuing Delay (Retraso de Cola) - **Variable**

Es el tiempo que el paquete pasa esperando dentro de un router antes de ser enviado. Es **variable** porque depende de qué tan saturada esté la red en ese momento.

- **Ejemplo:** Imagina que llegas a un peaje. Si no hay coches, pasas rápido; si hay tráfico, te toca esperar en la fila (cola).
    
### 4. Serialization Delay (Retraso de Serialización) - **Fijo**

Es el tiempo que tarda el router en "empujar" físicamente los bits del paquete hacia el cable. Depende directamente de la velocidad (ancho de banda) de la interfaz.

- **Ejemplo:** Si el cable es una manguera, este es el tiempo que tarda el agua en entrar por el agujero. Una manguera más ancha (más Gigabits) lo hace más rápido.
    
### 5. Propagation Delay (Retraso de Propagación) - **Variable**

Es el tiempo que tarda la señal eléctrica o de luz en recorrer el cable físico. Aunque la electricidad va casi a la velocidad de la luz, la distancia importa. Se marca como variable si la ruta física cambia (por ejemplo, si un enlace cae y el paquete toma un camino más largo).

- **Ejemplo:** El tiempo que tarda un mensaje en viajar de Madrid a Tokio por el cable submarino.
    
### 6. De-jitter Delay (Retraso de búfer de fluctuación) - **Fijo**

Como vimos antes, los paquetes pueden llegar a tiempos distintos (jitter). El receptor los guarda unos milisegundos en una "sala de espera" para ordenarlos y que el audio se escuche fluido.

- **Ejemplo:** Es como una fila de entrada a un cine donde el portero detiene a la gente un momento para que entren todos con el mismo ritmo y no a empujones.

![[Pasted image 20260427125734.png]]
El **jitter** es la variación en el tiempo de llegada de los paquetes de datos a través de una red. En términos simples, es la **irregularidad** o inestabilidad en el retraso de la red (latencia).

![[Pasted image 20260427125704.png|655]]

![[Pasted image 20260427125751.png|657]]