- Tags: #ipv6_subneting 

#### /64 Es la mascara de red Recomendada para direcciones IPv6 aunque no es obligatoria.

![[Pasted image 20260402230831.png]]


### La Estructura que te van a pedir en el examen

Generalmente, tu proveedor de internet (o el ejercicio del examen) te dará un bloque de red con un prefijo **/48**.

Una dirección IPv6 tiene 128 bits y se divide así cuando haces subnetting:

- **Prefijo Global (Bits 1 al 48):** Te lo da tu ISP o el ejercicio. No se toca.
    
- **ID de Subred (Bits 49 al 64):** ¡Aquí es donde juegas tú! Tienes 16 bits para crear hasta $65,536$ subredes diferentes.
    
- **ID de Interfaz / Host (Bits 65 al 128):** Los últimos 64 bits reservados para los dispositivos.
    

---

### 📝 Ejemplo Práctico paso a paso

Imagina que en Packet Tracer te dan esta red para tu empresa:

> **`2001:DB8:ABCD::/48`**

Y te piden crear **3 subredes** distintas: una para la red de Administradores, otra para los Servidores y otra para la red Wi-Fi.

Como queremos que cada subred sea una red estándar de tamaño `/64`, solo tenemos que empezar a contar en hexadecimal en el **cuarto bloque** de la dirección (el que va justo antes de los dos puntos dobles `::`).

Mira qué fácil se generan:

|**Subred**|**Dirección de Red IPv6**|**¿Por qué?**|
|---|---|---|
|**Subred 1 (Administración)**|`2001:DB8:ABCD:0001::/64`|Usamos el `1` en el cuarto bloque.|
|**Subred 2 (Servidores)**|`2001:DB8:ABCD:0002::/64`|Usamos el `2` en el cuarto bloque.|
|**Subred 3 (Wi-Fi)**|`2001:DB8:ABCD:0003::/64`|Usamos el `3` en el cuarto bloque.|

_(Nota: Como los ceros a la izquierda se pueden omitir, la Subred 1 también la puedes escribir de forma corta como `2001:DB8:ABCD:1::/64`)_.

---

### 💻 ¿Y cómo le pongo las IPs a los PCs de cada subred?

Para darle IP a los equipos dentro de esas redes, simplemente dejas fijo el prefijo `/64` de la subred y le pones un número al final (en los últimos 64 bits):

**En la Subred 1 (Administración):**

- IP para el Router (Puerta de enlace): `2001:DB8:ABCD:1::1`
    
- IP para el PC 1: `2001:DB8:ABCD:1::10`
    
- IP para el PC 2: `2001:DB8:ABCD:1::11`
    

**En la Subred 2 (Servidores):**

- IP para el Router: `2001:DB8:ABCD:2::1`
    
- IP para el Servidor Web: `2001:DB8:ABCD:2::50`
    

---

### ⚠️ El único truco: ¡Recuerda el Hexadecimal!

En IPv4 cuentas del 0 al 9 y luego pasas al 10. En IPv6, como es hexadecimal, la cuenta en el cuarto bloque va así:

`1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F` ... y después del `F` vendría el `10`.

¿Ves lo sencillo que es comparado con IPv4? No hay que calcular máscaras raras como `255.255.255.224`. Todas las subredes terminan en `/64`.

¿Quieres que hagamos un ejercicio rápido con otra red para ver si le has pillado el truco?


![[Pasted image 20260402234245.png|689]]![[Pasted image 20260402234321.png|689]]
![[Pasted image 20260402234541.png|689]]
![[Pasted image 20260402234632.png|689]]![[Pasted image 20260402234826.png|689]]![[Pasted image 20260402235035.png|691]]
![[Pasted image 20260402235239.png|694]]
![[Pasted image 20260402235614.png|701]]
![[Pasted image 20260402235632.png|701]]
![[Pasted image 20260402235700.png|701]]