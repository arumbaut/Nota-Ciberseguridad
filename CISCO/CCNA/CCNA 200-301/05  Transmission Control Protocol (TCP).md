- Tag: #tcp_ip  #netstat

TCP es un protocolo de la **Capa de Transporte [4]** utiliza el mecanismo de **Three Way Handshake** 

![](../../../attachments/image20250526095118.png)

#### **Para terminar una conexión TCP establecida:**
![](../../../attachments/image20250526095238.png)

### Port Numbers
##### Los puertos son : Conocidos ,Registrados , Dinamicos o Privados

![[Pasted image 20260401113002.png|720]]



Examinar sesiones TCP activas con netstat.
```cmd

netstat -help

netstat

netstat -n 

netstat -n 1   #Actualiza cada 1 segundo

netstat -na    #Muestra los puertos de escucha de nuestra pc [a]

netstat -nap TCP  #Muestra los puertos de escucha de nuestra pc solo los TCP [p] restringe la conexion a TCP

netstat -naop TCP  #Muestra los puertos de escucha de nuestra pc solo los TCP y parametro [o] le agrega el Process ID (PID)

netstat -naobp TCP  #Muestra los puertos de escucha de nuestra pc solo los TCP le agrega el Process ID (PID) y ademas con el parametro [b] nos muestra que programa esta utilizando la conexion

netstat -r #Muestra la tabla de rutas de la PC

```


## 1. El Establecimiento y Cierre de Sesión (Handshake)

Para que dos computadoras hablen por TCP, primero deben ponerse de acuerdo. Es como cuando llamas por teléfono: no empiezas a hablar hasta que la otra persona dice "hola".

- **Establecimiento (Three-Way Handshake):** Se menciona brevemente al principio. Utiliza los mensajes `SYN`, `SYN-ACK` y `ACK` para abrir el canal de comunicación.
    
- **Cierre de Sesión (Fin / Fin-Ack):** Al final, cuando el servidor ya no tiene más datos que enviar (no existe el siguiente byte), envía un mensaje con la bandera `FIN`. Ambas máquinas se responden con `FIN-ACK` para cerrar la llamada educadamente y liberar los recursos.
    

---

## 2. Segmentación de Datos (El tamaño importa)

- **Concepto:** No puedes enviar un archivo gigante (como una imagen) de un solo golpe porque saturarías la red o excederías los límites físicos del cable.
    
- **Explicación:** TCP agarra ese archivo y lo pica en pedacitos llamados **Segmentos**. 
    
- **MMS (Maximum Segment Size):** Lo máximo que puedes meter en un segmento normal son **$1460$ bytes**.
    

---

## 3. Números de Secuencia y Acuse de Recibo (ACK)

Esta es la magia que hace que TCP sea "confiable". Si un paquete se pierde por el camino, TCP se da cuenta y lo vuelve a enviar.

- **Sequence Number (Número de Secuencia):** Es una etiqueta que le dice al receptor: _"Oye, este pedazo de información que te mando empieza en el byte número X"_. Así, la computadora que recibe los datos sabe cómo ordenar las piezas del rompecabezas aunque lleguen desordenadas.
    
- **Acknowledgement Number (Número de Reconocimiento / ACK):** Es la respuesta del receptor. Lo curioso de TCP es que el número de ACK no es el número que recibió, **sino el número del siguiente byte que está esperando**. Si recibe los bytes del $1$ al $1250$, el cliente responde con un $ACK\ 1251$ (indicando: _"Recibí todo perfecto hasta el $1250$, ahora mándame el $1251$"_ ).
    

---

## 4. SACK (Selective Acknowledgement / Reconocimiento Selectivo)

- **¿Qué pasa si se pierde un paquete en el medio?** Imagina que el servidor manda los bytes del $2501$ al $3750$, y luego los del $3751$ al $5000$. Pero el primer paquete se pierde en la red.
    
- **Explicación:** El cliente recibe el segundo paquete ($3751$ al $5000$) y se da cuenta de que le falta el hueco anterior. En lugar de pedir que le reenvíen todo desde el principio, manda un **SACK**. Le dice al servidor: _"Oye, tengo hasta el byte $2500$ y también tengo del $3751$ al $5000$. Por favor, solo reenvíame el hueco que me falta ($2501$ al $3750$)"_. Esto hace que internet sea infinitamente más rápido y eficiente.

### Aplicándolo a tu ejemplo :

Imagina que el servidor le manda al cliente el primer pedazo de la imagen de la Tierra:

- **El Servidor manda:** Una caja con los bytes del **1 al 1250**. El número de secuencia de este paquete es `Seq: 1` (porque empieza en el byte 1).
    
- **El Cliente recibe:** Abre la caja y ve que todo está perfecto del 1 al 1250.
    
- **El Cliente responde con un ACK:** El cliente calcula: "Recibí hasta el 1250. El siguiente que necesito es el **1251**". Así que manda un paquete con un `Ack: 1251`

### ¿Qué hace el servidor ahora?

Cuando el servidor lee ese `Ack: 1251`, entiende el mensaje alto y claro: _"Perfecto, el cliente ya tiene hasta el 1250, ahora le voy a mandar el siguiente bloque"_.

Por lo tanto, el siguiente paquete del servidor tendrá:

- **`Seq: 1251`** (Porque arranca justo en el byte que el cliente le pidió).
    
- El paquete llevará los bytes del **1251 al 2500**.
    

Y cuando el cliente reciba ese paquete con éxito, su siguiente respuesta será un **`Ack: 2501`**. ¡Y así sucesivamente hasta terminar el archivo


### Las 2 piezas de información que usa el receptor

Cuando a tu computadora le llega un paquete de datos por la red, ese paquete viene en una "caja" que trae etiquetas. Para calcular el siguiente `ACK`, el receptor mira dos etiquetas:

1. **El Número de Secuencia (`Seq`):** Que le dice dónde empieza.
    
2. **El Tamaño de los Datos (Payload Length):** Que le dice cuántos bytes de información real vienen dentro de esa caja. (La tarjeta de red mide físicamente cuántos bytes llegaron).

### La Fórmula Matemática de TCP

Para saber cuál es el último byte recibido y calcular el número de `ACK` (el que está esperando a continuación), el receptor simplemente aplica esta fórmula:

Siguiente ACK = Número de Seq + Tamaño de los Datos

### Wireshark
En la comunicacion  stream entre 2 dispositivos en wireshark lo escrito en rojjo es lo enviado del dispositivo origen y lo escrito en azul es lo enviado por el dispositivo de destino

![[Pasted image 20260401144003.png]]