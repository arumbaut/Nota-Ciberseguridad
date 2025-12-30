```
mi_diccionario={"nombre":"Adrian","apellido":"Alonso","edad":28}

print(mi_diccionario.nombre)

Add elementos al dicc
mi_diccionario["apellido_dos"]="Rumbaut"

Eliminar elemeno 
del mi_diccionario["apellido_dos"]

Recorrer el diccionario

for key,value in mi_diccionario.items():
	instrucciones
	
Limpiar dicc
mi_diccionario.clear()

Diccionario de cuadrados
cuadrados={x: x**2 for x in range(6)}

Listar todas las claves
cuadrados.key()
Listar todas los valores
cuadrados.values()

Funcion get para hacer busquedas
mi_diccionario.get("nombre","No encontrado")
```


**Características de los Diccionarios**

- **Desordenados**: Los elementos en un diccionario no están ordenados y no se accede a ellos mediante un índice numérico, sino a través de claves únicas.
- **Dinámicos**: Se pueden agregar, modificar y eliminar pares clave-valor.
- **Claves Únicas**: Cada clave en un diccionario es única, lo que previene duplicaciones y sobrescrituras accidentales.
- **Valores Accesibles**: Los valores no necesitan ser únicos y pueden ser de cualquier tipo de dato.

**Operaciones con Diccionarios**

Durante la clase, exploraremos cómo realizar operaciones básicas y avanzadas con diccionarios:

- **Agregar y Modificar**: Cómo agregar nuevos pares clave-valor y modificar valores existentes.
- **Eliminar**: Cómo eliminar pares clave-valor usando del o el método ‘**pop()**‘.
- **Métodos de Diccionario**: Utilizar métodos como ‘**keys()**‘, ‘**values()**‘, y ‘**items()**‘ para acceder a las claves, valores o ambos en forma de pares.
- **Comprensiones de Diccionarios**: Una forma elegante y concisa de construir diccionarios basados en secuencias o rangos.

**Uso de Diccionarios en Python**

- **Almacenamiento de Datos Estructurados**: Ideales para almacenar y organizar datos que están relacionados de manera lógica, como una base de datos en memoria.
- **Búsqueda Eficiente**: Los diccionarios son altamente optimizados para recuperar valores cuando se conoce la clave, proporcionando tiempos de búsqueda muy rápidos.
- **Flexibilidad**: Pueden ser anidados, lo que significa que los valores dentro de un diccionario pueden ser otros diccionarios, listas o cualquier otro tipo de dato.