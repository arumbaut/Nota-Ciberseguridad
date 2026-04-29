- Tags: #standard_acl_conf

![[Pasted image 20260427162530.png|747]]

Podemos crear ACL Standard con números desde *1 - 99 o 1300 - 1999* 


```cisco
Router(config)#ip access-list standard DEMO  #Creamos la lista

Router(config-std-nacl)#permit 10.0.0.16 0.0.0.255   #Podemos permitir una red como este caso

Router(config-std-nacl)#permit host 10.0.0.16 #Podemos permitir un unico host como este ejemplo

Router(config-std-nacl)#deny deny  #Por ultimo denegamos todo el trafico

Router(config-std-nacl)#exit
Router(config)#intereface F0/1              #Entramos a la interace
Router(config-if)#ip access-group DEMO out  #Aplicamos la acl a la interface

```

Podemos crear ACL Standard con números desde *1 - 99 o 1300 - 1999* 

```cisco
Router(config)#access-list 10 permit 10.0.0.16 0.0.0.255   #Creamos la lista

Router(config-std-nacl)#access-list 1800 permit host 10.0.0.16 #Podemos permitir un unico host como este ejemplo
```

Las reglas en las access-list se les asigna un numero de secuencia por si queremos modificarlas y poner reglas antes que otras podemos verlas con el comando `show access-list`

Para poner una regla encima de una que ya este pues debemos ponerle delante un numero menor a la nueva regla que el que tiene la regla que ya esta. Eje Si tenemos una regla con un numero de secuencia 10 la nueva se pondría delante y esto es muy importante porque las ACL se leen de forma secuencial así que si una regla superior deniega un trafico este no funcionara aunque una regla inferior la permita por estar denegada previamente

```cisco
Router(config-std-nacl)# 5 permit 192.168.1.10 0.0.0.0
```


### 1. El objetivo

Querían crear una wildcard que cubra **exactamente** dos direcciones: `10.0.0.16` y `10.0.0.17`.

### 2. Comparación Binaria

Para saber qué wildcard usar, escribieron ambas IPs en binario y compararon bit por bit:

- **10.0.0.16:** termina en `...00010000` (el último bit es **0**)
    
- **10.0.0.17:** termina en `...00010001` (el último bit es **1**)
    

Si te fijas en la imagen, todos los bits son **idénticos** (en color azul) excepto el último bit (en color verde).

### 3. La lógica del Wildcard en binario

Aquí está el truco que usaron:

- Donde los bits son **iguales**, en la Wildcard se pone un **0** (significa: "este bit tiene que ser exactamente así").