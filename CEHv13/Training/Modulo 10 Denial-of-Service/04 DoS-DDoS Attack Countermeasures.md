#### Detection Techniques 
#### ▪ Activity Profiling 
El perfilado de actividad analiza el tráfico de red mediante la tasa promedio de paquetes en flujos con cabeceras similares (IP, puertos, protocolos). Un posible ataque DDoS se detecta por:

- Aumento de actividad en flujos de red.
    
- Mayor número de flujos distintos.
    

También se analiza la **entropía** (nivel de aleatoriedad): si aumenta, puede indicar un ataque. Para manejar el alto volumen de datos, se agrupan flujos similares. Un incremento en la tasa de paquetes o en su diversidad puede señalar un ataque DoS.

#### ▪ Sequential Change-Point Detection

- Filtra el tráfico por IP, puerto y protocolo.
    
- Usa un gráfico tiempo/tasa de flujo para visualizar el tráfico.
    
- Detecta ataques DoS al identificar cambios bruscos en el flujo.
    
- Utiliza el algoritmo **CUSUM** para detectar desviaciones.
    
- También identifica actividades de **gusanos de red** (scanning).

