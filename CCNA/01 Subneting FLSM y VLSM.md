
### FSLM

#### Fixed Length Subnet Mask
**FLSM** es un método de direccionamiento donde **todas las subredes tienen exactamente el mismo tamaño**.
Imagina que tienes una pizza (una red grande) y decides cortarla en 4 trozos. Con FLSM, los 4 trozos tienen que ser **idénticos** en tamaño, sin importar si en un trozo solo va a comer una persona y en otro van a comer cinco.

## Características Principales

- **Máscara Única:** Todas las subredes comparten la misma máscara de subred (por ejemplo, todas son `/26`).
    
- **Desperdicio de IPs:** Es su mayor desventaja. Si una subred necesita 50 IPs y otra solo necesita 2, en FLSM ambas recibirán un bloque de (por ejemplo) 64 IPs. Las 62 IPs sobrantes en la segunda subred se pierden.
    
- **Simplicidad:** Es mucho más fácil de administrar y configurar porque no hay que hacer cálculos diferentes para cada segmento.


### VLSM

Es una técnica que permite aplicar **diferentes máscaras de subred** a diferentes segmentos de una misma red principal. Esto significa que puedes tener una subred de 100 equipos, otra de 10 y otra de solo 2, dándole a cada una el tamaño justo que necesita.

**Su objetivo principal es evitar el desperdicio de direcciones IP.**


### Componentes claves de una subred

#### Dirección de red :   Network ID identificador de la red  *(Primera dirección IP de la red)*
#### Direcciones Utilizables :   Direcciones de Hosts
#### Direcciones Broadcast :   *Ultima IP de la subred*
#### Mascara de Subred :   Direcciones de Hosts



La dirección de *red* la obtenemos poniendo todos los *bits* de *HOST* a 0
La dirección de *broadcast* la obtenemos poniendo todos los *bits* de la porcion de *HOST* a 1
Las direcciones de *Hosts*  siempre se calculan 2^n-2   donde *n* es el valor de los bits para *HOST* .

Ejemplo

10.10.10.0     /24

Tenemos 24 bits para la subred 
Para  los bits de*HOST*   hacemos el calculo de *32-24= 8* , Recordemos que las direcciones *IP* se conforman de 4 octetos por eso el calculo.
#### Entoces tenemos que:
*Direccion de red*: Ponemos todos los bits destinados a host a 0 y obtenemos
10.10.10.0

*Direccion de Broadcast*: Ponemos todos los bits destinados a host a 1 y obtenemos
10.10.10.255


### Ejercicion:

Tenemos la red *192.168.1.0 / 24*  nos piden dividirla en 4 subredes utilizando  *FLSM*

### Formula de subredes
1- Tenemos 24 bits para red y 8 para host , lo que nos lleva que podemos utilizar bits de host para las nuevas subredes que crearemos al ser 4 subredes pues nececitaremos 2^n >= redes solicitadas, donde n son los bits que utilizaremos de la porcion de hosts.

En este caso 
2^2 >= 4
4=4

Entonces deducimos que las nuevas mascara seria un */26*  ya que le cogimos 2 bits de la porcion de host
Las redes serian entonces
Tomamos el octeto que modificamos y vamos generando las combinaciones con los bits tomados para red, y sumamos su valor esto nos da el valor de la red , para ver el broadcast ponemos los bit de hos de la red a 1.
. *128 64* 32 16 8 4 2 1
   0      0   0   0  0 0 0 0      Red 192.168.1.0  /26
   0      0   1    1   1  1  1  1      Broadcast 192.168.1.63
   
   0      1    0   0  0 0 0 0      Red 192.168.1.64  /26
   0      1    1    1   1  1  1  1      Broadcast 192.168.1.127
   
   1       0   0   0  0 0 0 0      Red 192.168.1.128  /26
   1       0    1    1  1  1  1  1      Broadcast 192.168.1.191

   1       1    0   0  0 0 0 0      Red 192.168.1.192  /26
   1       1    1    1  1  1  1  1      Broadcast 192.168.1.255
   
*192.168.1.0 - 192.168.1.63 / 26*
*192.168.1.64 192.168.1.127 / 26*
*192.168.1.128 192.168.1.191/ 26*
*192.168.1.192 - 192.168.1.255 / 26*


Truco para calcular el incremento de las subredes, llevamos el octeto que varia a binario en el caso que nos ocupa como pedimos dos bits de host nos queda

           128 64 32 16 8 4 2 1    
255.255.255. 1       1     0    0    0  0  0  0

255.255.255. 192

Incremento de subredes = 256 - mascara generada
Incremento de subredes = 256 - 192 
Incremento de subredes = 64		

*192.168.1.0 - 192.168.1.63 / 26*
*192.168.1.64 192.168.1.127 / 26*
*192.168.1.128 192.168.1.191/ 26*
*192.168.1.192 - 192.168.1.255 / 26*


### VLSM 
Para ahorrar la mayor cantidad de red
Ejercicio
Nos dan una red *150.186.0.0 /24*  y la siguiente topologia
![](../../attachments/Pasted%20image%2020260325064318.png)

Debemos calcular el direccionamiento para cada una de las 5 subredes que se necesitan.

1 - Primero ordenamos de mayor a menor la cantidad de host necesarios por subred
2 - Para calcular la Subnet Mask utilizaremos la formula  *2^n -2 >=75* para cada una de las subredes
3 - Calculamos la mascara de subred basados en el valor de n = 7 por lo tanto la nececitamos 1 bit de la porción de host  por lo que nuestra mascara cambia de barra /24 a /25 , tambien lo podemos calcular como 32 - n 
4 - Calculamos el incremento de la red lo calculamos con 256 - suma de los octetos que varían, en este caso solo varia un octeto el de 128. Por lo que el incremento es en 128 

Hacemos el procedimiento anterior para cada una de las subredes

2^n -2 >=50      n =6      32-n = mask    32 - 6 = 26

Paso 4
256 -(128 + 64)=  
256 - 192 = 64 


2^n -2 >=15      n =5      32-n = mask    32 - 5 = 27

256 -(128 + 64+32)=  
256 - 224 = 32 

2^n -2 >=2      n =2     32-n = mask    32 - 2 = 30

256 -(128 + 64+32+16+8+4)=  
256 - 252 = 4 

| Host | Subnet Mask      | Red           | Broadcast        | Rango de IPs Utilizables      | Incremento de la red |
| ---- | ---------------- | ------------- | ---------------- | ----------------------------- | -------------------- |
| 75   | 150.186.0.0 /25  | 150.186.0.0   | 150.186.0.127    | 150.186.0.1-150.186.0.126     | 128                  |
| 50   | 150.186.0.128/26 | 150.186.0.128 | 150.186.0.191    | 150.186.0.129 - 150.186.0.190 | 64                   |
| 15   | 150.186.0.192/27 | 150.186.0.192 | 150.186.0.223    | 150.186.0.193 - 150.186.0.222 | 32                   |
| 2    | 150.186.0.224/30 | 150.186.0.224 | 150.186.0.227/30 | 150.186.0.225-150.186.0.226   |                      |
| 2    | 150.186.0.228/30 | 150.186.0.228 | 150.186.0.231    | 150.186.0.229-150.186.0.230   |                      |
