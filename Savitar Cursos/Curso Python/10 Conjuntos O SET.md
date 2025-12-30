
```
#!/usr/bin/env python3

mi_conjunto={1,2,3,4,5}
mi_segundo_conjunto={4,5,6,7,8}
mi_conjunto.update({8,9,10})

Para si no estas seguro de que el elemento esta en el conjunto 
mi_conjunto.discard(10)

Si sabes que exiiste en el conjunto
mi_conjunto.remove(10)


Interseccion
intersection_conjunto=mi_conjunto.intersection(mi_segundo_conjunto)

Union
intersection_conjunto=mi_conjunto.union(mi_segundo_conjunto)

Saber si un conjunto es subconjunto de otro conjunto
intersection_conjunto=mi_conjunto.issubset(mi_segundo_conjunto)

admin={"Adrian Alonso","Yeniset Delfino","Rene Rumbaut","Barbara Milagro"}
usersTec={"Yeniset Delfino","Rene Rumbaut"}
print(usersTec.issubset(admin))
>>>True

```

Sirven para eliminar elementos repetidos 
```
mi_lista=[1,2,4,6,4,7,4,7,3,3,7,]
mi_lista_no_repeat=list(set(mi_lista))
```


**Características de los Conjuntos**

- **Unicidad**: Los conjuntos automáticamente descartan elementos duplicados, lo que los hace perfectos para recolectar elementos únicos.
- **Desordenados**: A diferencia de las listas y las tuplas, los conjuntos no mantienen los elementos en ningún orden específico.
- **Mutabilidad**: Los elementos de un conjunto pueden ser agregados o eliminados, pero los elementos mismos deben ser inmutables (por ejemplo, no puedes tener un conjunto de listas, ya que las listas se pueden modificar).

**Operaciones con Conjuntos**

Exploraremos las operaciones básicas de conjuntos que Python facilita, como:

- **Adición y Eliminación**: Añadir elementos con ‘**add()**‘ y eliminar elementos con ‘**remove()**‘ o ‘**discard()**‘.
- **Operaciones de Conjuntos**: Realizar uniones, intersecciones, diferencias y diferencias simétricas utilizando métodos o operadores respectivos.
- **Pruebas de Pertenencia**: Comprobar rápidamente si un elemento es miembro de un conjunto.
- **Inmutabilidad Opcional**: Usar el tipo ‘**frozenset**‘ para crear conjuntos que no se pueden modificar después de su creación.

**Uso de Conjuntos en Python**

- **Eliminación de Duplicados**: Son útiles cuando necesitas asegurarte de que una colección no tenga elementos repetidos.
- **Relaciones entre Colecciones**: Facilitan la comprensión y el manejo de relaciones matemáticas entre colecciones, como subconjuntos y superconjuntos.
- **Rendimiento de Búsqueda**: Proporcionan una búsqueda de elementos más rápida que las listas o las tuplas, lo que es útil para grandes volúmenes de datos.