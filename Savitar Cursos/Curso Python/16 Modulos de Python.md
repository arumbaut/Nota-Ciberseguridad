Importacion de diferentes archivos librerias paquetes

```
Creamos el archivo math.py con vrias funciones con funciones aritmeticas

math_operation.py 


Creamos main.py e importamos  math.py para reutilizar el codigo

Importacion , lo busca en el mismo directorio 

#Opciones
1- import math_operation
2- from math_operation import *
3- from math_operation import fun1, fun2, fun3 || from math_operation import fun1 as f1

```

Bibliotecas estandars
```
import math || import math as m
import hashlib
print(dir(math)) #Lista todas las propiedades y funciones de la libreria
```

Buscar si donde esta el modulo 
```
print(hashlib.__file__) #nos muestra el archivo correspondiente para el modulo

si fuera una libreria integrada a python no nos lo muestra
```

Libreria sys
```
import sys
import hashlib
print(sys.path)
print(hashlib.__file__)

```