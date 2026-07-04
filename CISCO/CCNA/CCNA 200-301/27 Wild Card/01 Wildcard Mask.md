Con la Wildcard Masks no siempre podemos seleccionar el rango exacto que buscamos

Ejemplo tenemos este rango *10.0.0.64 - 10.0.079*.

Para seleccionar un Wildcard Mask para este rango:
- Seleccionamos  la primera dirección IP y la llevamos a binario. 
- Seleccionamos  la ultima dirección IP y la llevamos a binario.   
- Comparamos cada uno de los bits de izquierda a derecha haste encontrarnos un bit diferente
- En la Wilcard MASK todos los bits iguales antes del bit diferente se establecen a 0 y todos los bits a partir del bit diferente se establecen a 1 

![[Pasted image 20260428065521.png|803]]

![[Pasted image 20260428065813.png|807]]

### 1. El problema del "rango sucio"

El objetivo es cubrir desde la IP **10.0.0.14 hasta la 10.0.0.99**.

- Como este rango no se ajusta a una máscara de subred estándar (como una /24 o /27), no existe **una sola** Wildcard Mask que cubra exactamente desde la .14 a la .99 sin pasarse o quedarse corta.
    
![[Pasted image 20260428071145.png|751]]
### 2. La solución: Dividir para vencer

Para solucionar esto, se divide el gran rango en "bloques" que el router sí pueda entender de forma binaria. Para llegar de la .14 a la .99, crea 5 reglas:

1. **Bloque 1 (.14 a .15):** Usa la wildcard `0.0.0.1` (Cubre 2 IPs).
    
2. **Bloque 2 (.16 a .31):** Usa la wildcard `0.0.0.15` (Cubre 16 IPs).
    
3. **Bloque 3 (.32 a .63):** Usa la wildcard `0.0.0.31` (Cubre 32 IPs).
    
4. **Bloque 4 (.64 a .95):** Usa otra vez `0.0.0.31` (Cubre otras 32 IPs).
    
5. **Bloque 5 (.96 a .99):** Usa la wildcard `0.0.0.3` (Cubre las últimas 4 IPs).
    

### 3. ¿Cómo se calcula cada bloque? (Lógica Binaria)

Se escribe la IP de inicio y la IP final en binario y busca hasta dónde son **idénticas**:

- Si los bits son iguales, la wildcard lleva un **0**.
    
- En cuanto un bit cambia, a partir de ahí hacia la derecha, la wildcard lleva **1** (que significa "no me importa este bit").
    

**Ejemplo corto de la imagen (.16 y .17):**

- **.16** termina en `...00010000`
    
- **.17** termina en `...00010001`
    
- Como solo cambia el último bit, la wildcard es `0.0.0.1` (el 1 al final representa ese bit que cambió).

La clave para entenderlo es que **los routers solo pueden procesar bloques que son potencias de 2** (1, 2, 4, 8, 16, 32, 64, 128...).

Si tú le pides al router un rango que no es una potencia de 2 exacta (como del .14 al .99), el router "no sabe" hacerlo en una sola línea. Es como si intentaras comprar exactamente 86 huevos usando solo cajas de 12, de 6 o de 30; tendrías que combinar varias cajas para llegar al número exacto.

Aquí tienes la explicación paso a paso de cómo se "rellena" ese rango:

### 1. El concepto de "Bloques Binarios"

Un wildcard mask siempre define un bloque de direcciones. Por ejemplo:

- `0.0.0.1` = Bloque de **2** IPs.
    
- `0.0.0.3` = Bloque de **4** IPs.
    
- `0.0.0.7` = Bloque de **8** IPs.
    
- `0.0.0.15` = Bloque de **16** IPs.
    
- `0.0.0.31` = Bloque de **32** IPs.
    

### 2. Cómo se dividió el rango del video (10.0.0.14 al 10.0.0.99)

Para cubrir ese rango sin dejar huecos y sin pasarse, el autor hizo lo siguiente:

1. **Primero, completar el número pequeño:** Empezó en la `.14`. El bloque más pequeño para avanzar es de 2 IPs (`0.0.0.1`). Así cubre la `.14` y la `.15`.
    
2. **Segundo, usar bloques grandes:** Ahora que está en la `.16`, puede usar un bloque de 16 IPs (`0.0.0.15`), lo que lo lleva hasta la `.31`.
    
3. **Tercero, el bloque más grande posible:** Saltó a la `.32` y usó un bloque de 32 IPs (`0.0.0.31`), llegando a la `.63`.
    
4. **Cuarto, otro bloque grande:** Desde la `.64` usó otro bloque de 32 IPs (`0.0.0.31`), llegando a la `.95`.
    
5. **Quinto, cerrar el rango:** Como solo le faltaba llegar a la `.99`, usó un bloque de 4 IPs (`0.0.0.3`) que cubre la .96, .97, .98 y .99.
    

### 3. ¿Por qué se hace así?

Si intentaras usar una sola wildcard mask muy grande desde el principio (por ejemplo, una que cubra 128 IPs), empezarías en la `10.0.0.0` y terminarías en la `10.0.0.127`. **Eso es un error**, porque estarías bloqueando o permitiendo IPs (como la .5 o la .110) que no estaban en tu plan original.