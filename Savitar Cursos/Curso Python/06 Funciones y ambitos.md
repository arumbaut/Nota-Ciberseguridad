```
def saludo(nombre):
	instrucciones
	

Llamada a funcion
saludo("Manuel")
```

Funciones Lambda
```
mi_funcion= lambda:"Mi funcion"

print(mi_funcion())

cuadrado=lambda x: x**2

print(cuadrado(5))

num=[1, 2, 3, 6, 7, 8]

cuadrados= map(lambda x: x**2,num)

pares= filter(lambda x: x%2 ==0,num)
```

Modulos
```
from functools import reduce

num=[1,2,3,4,5,6]

multiply= reduce(lambda x,y: x*y , num)
```