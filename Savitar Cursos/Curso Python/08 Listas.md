Conjunto de datos mutables

```
#!/usr/bin/env python3

mi_lista=[1,2,3,4,5]

Ordenar
mi_lista.sort()

Invertir
mi_lista.reverse()

attacks=["Phishing","Dos","DDos","click jacking"]

attack_upper= [attack.uppercase() for attack in attacks]

attack_lower= [attack.lower() for attack in attacks]


```

**Operaciones con Listas**
- Añadir elementos con métodos como ‘**append()**‘ y ‘**extend()**‘.
- Eliminar elementos con métodos como ‘**remove()**‘ y ‘**pop()**‘.
- Ordenar las listas con el método ‘**sort()**‘ o la función incorporada ‘**sorted()**‘.
- Invertir los elementos con el método ‘**reverse()**‘ o la sintaxis de corte ‘**[::-1]**‘.
- Comprender las comprensiones de listas, una forma “pythonica” de crear y manipular listas de manera concisa y eficiente.

```
zip tine la capacidad de unificar los elementos de los arreglos en el frmato
('Adri', 23)

nombre=["Adri","Yai","Yeni","Rene"]
edades=[23,45,66,78]

for name, edad in zip(nombre,edades):
	print(f"Nombre: name ---> edad {edad}")
```