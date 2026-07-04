

Radiofrecuencia para redes **Wi-Fi 802.11** en la banda de **2.4 GHz**, explicando por qué es crucial evitar el solapamiento de canales para garantizar una conexión estable.


![[Pasted image 20260503234046.png|889]]

### 1. El ancho de banda de los canales

Para que el estándar 802.11 envíe datos de manera efectiva, requiere **22 MHz de ancho de banda**. Aunque cada canal está separado por solo 5 MHz, el protocolo necesita ocupar un espacio mayor para funcionar correctamente.

- **Ejemplo:** Si configuras un punto de acceso (AP) en el **Canal 1**, este no solo usa la frecuencia central del canal 1, sino que se extiende por el espectro ocupando también lo que correspondería a los canales 2 y 3.
    

### 2. Canales que no se solapan (Non-overlapping channels)

Debido a que cada canal "invade" el espacio de los canales adyacentes, en la mayor parte del mundo solo existen **tres canales** en la banda de 2.4 GHz que pueden funcionar simultáneamente sin interferir entre sí:

- **Canal 1**.
    
- **Canal 6**.
    
- **Canal 11**.
    

Cualquier otra combinación (por ejemplo, usar el canal 1 y el canal 2 al mismo tiempo en el mismo lugar) causará interferencias y problemas de comunicación.

### 3. El problema del solapamiento

Cuando varios puntos de acceso operan en el mismo canal o en canales que se solapan (interferencia de canal adyacente), los dispositivos como laptops se confunden.

- **Confusión del cliente:** El dispositivo puede intentar conectarse a un AP lejano con señal débil en lugar de uno cercano, o tratar de comunicarse con varios a la vez.
    
- **Problemas de red:** Los paquetes de información se mezclan y los puntos de acceso no pueden distinguir las señales, provocando una caída drástica en el rendimiento de la red.
    

### 4. Diseño de "Capa de Cobertura" (Blanket of coverage)

En entornos grandes con múltiples puntos de acceso, la solución es asignar canales únicos a los AP que estén físicamente cerca unos de otros. La clase utiliza un ejemplo de colores para visualizarlo:

- **Verde:** Canal 1.
    
- **Azul:** Canal 6.
    
- **Naranja:** Canal 11.
    

Al alternar estos canales, te aseguras de que un dispositivo siempre se conecte al AP con la señal más fuerte sin que otros AP cercanos en el mismo canal causen interferencia.

**Regla de oro:** Los puntos de acceso adyacentes deben operar siempre en canales únicos que no se solapen.

![[Pasted image 20260503234237.png]]