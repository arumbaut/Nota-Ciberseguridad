![[Pasted image 20260503234849.png]]


![[Pasted image 20260503235322.png]]
Esta clase analiza el espectro de **Wi-Fi de 5.0 GHz** utilizado en el estándar 802.11, destacando sus ventajas sobre la banda de 2.4 GHz, especialmente en cuanto a la disponibilidad de canales.

### Resumen de puntos clave y ejemplos:

#### 1. Mayor disponibilidad de canales

A diferencia de la banda de 2.4 GHz, el espectro de 5 GHz ofrece muchísimos más canales utilizables.

- **Rango de frecuencia**: Comienza en **5.170 GHz** y sube hasta los **5.835 GHz**.
    
- **Identificación de canales**: En lugar de enumerarlos de uno en uno (como 1, 2, 3...), se identifican directamente los canales utilizables con una separación mayor, como el **36, 40, 44, 48**, etc.
    
- **Ventaja**: Tener más canales facilita enormemente el despliegue de redes sin que los canales se solapen entre sí.
    

#### 2. Canales reservados y DFS (Selección Dinámica de Frecuencia)

Existen rangos de canales (como los situados entre el 64 y el 100, o entre el 140 y el 149) que están reservados para aplicaciones militares o de radar. Sin embargo, se pueden usar bajo ciertas condiciones:

- **DFS (Dynamic Frequency Selection)**: Es una tecnología que permite a tu sistema Wi-Fi utilizar esos canales reservados siempre que no detecte un uso prioritario (militar o radar) en la zona.
    
- **Funcionamiento**: Si el sistema detecta una señal de radar o militar en uno de esos canales, debe cambiar automáticamente a un canal libre fuera de ese rango de forma inmediata.
    
- **Ejemplo**: Los controladores inalámbricos de Cisco suelen incluir esta tecnología integrada para aprovechar al máximo el espectro disponible.
    

#### 3. Uso doméstico vs. Profesional

La cantidad de canales que realmente puedes usar depende del equipo que tengas:

- **En casa**: Lo más probable es que solo utilices los rangos estándar, como los canales **36 al 48** y **149 al 161**.
    
- **En empresas**: Con hardware especializado (como controladores inalámbricos), se pueden habilitar los canales DFS para tener más opciones y evitar interferencias en entornos densos.
    

---

### Comparación rápida: 2.4 GHz vs. 5 GHz

|**Característica**|**2.4 GHz**|**5 GHz**|
|---|---|---|
|**Canales sin solapamiento**|Solo 3 (1, 6, 11)|Muchos más (36, 40, 44...)|
|**Interferencias**|Muy alta (pocos canales)|Baja (más espacio disponible)|
|**Tecnología especial**|Estática|DFS (para canales militares)|

**Explicación técnica para tu aprendizaje**: En ciberseguridad y administración de sistemas, preferimos la banda de 5 GHz en oficinas porque permite que muchos empleados se conecten a diferentes puntos de acceso cercanos sin que las señales choquen entre sí, manteniendo la **Disponibilidad** (uno de los pilares de la tríada **CIA** que mencionamos antes).