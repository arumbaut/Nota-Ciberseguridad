
```
#w write :Sobreescribe el archivo
#r read
#a append : Adiciona al archivo  
f= open("ejemplo.txt","w")

f.write("Hola mundo")

#Cerrar el archivo
f.close()
```

Forma mas optima y nos protege de errores ademas python se encarga de cerrar el archivo 
```
with open("ejemplo.txt","w") as f:
	f.write("Hola que tal!")
	
#Escribir multiples lineas
mis_lineas=["Primera","Segunda","Tercera"]	

with open("ejemplo.txt","w") as f:
	f.writelines(mis_lineas)
```

Para leer

```
with open("ejemplo.txt","r") as f:
	file_content=f.read()

print(file_contetnt)

#Leer linea por linea
with open("ejemplo.txt","r") as f:
	for line in f:
		print(line.strip())

#Leer una linea
with open("ejemplo.txt","r") as f:
	primera_linea=f.readline()

print(primera_linea)
```

Copiar un archivo
```
with open("/home/s4vitar/Desktop/S4vitar/Fondos/fondo.png", "rb") as f_in, open("image.png", "wb") as f_out:
    file_content = f_in.read()
    f_out.write(file_content)
```


Manejar excepcion cuando no existe el archivo
```
try:
    with open("prueba.txt", "r") as f: 
       print(f.read()) 
except FileNotFoundError: 
       print("\n[!] No ha sido posible encontrar este archivo")
```

**Manejo Básico de Archivos**

Explicaremos cómo utilizar la función ‘**open()**‘ para crear un objeto archivo y cómo los modos de apertura (‘**r**‘ para lectura, ‘**w**‘ para escritura, ‘**a**‘ para añadir y ‘**b**‘ para modo binario) afectan la manera en que trabajamos con esos archivos.

**Lectura de Archivos**

Detallaremos cómo leer el contenido de un archivo en memoria, ya sea de una sola vez con el método ‘**read()**‘ o línea por línea con ‘**readline()**‘ o iterando sobre el objeto archivo.

**Escritura en Archivos**

Examinaremos cómo escribir en un archivo usando métodos como ‘**write()**‘ o ‘**writelines()**‘, y cómo estos métodos difieren en cuanto a su manejo de strings y secuencias de strings.

**Manejadores de Contexto**

Uno de los aspectos más importantes de la lectura y escritura de archivos en Python es el uso de manejadores de contexto, proporcionados por la declaración ‘**with**‘. Los manejadores de contexto garantizan que los recursos se manejen correctamente, abriendo el archivo y asegurándose de que, sin importar cómo o dónde termine el bloque de código, el archivo siempre se cierre adecuadamente. Esto ayuda a prevenir errores comunes como fugas de recursos o archivos que no se cierran si ocurre una excepción.

El uso de ‘**with open()**‘ no solo mejora la legibilidad del código, sino que también simplifica el manejo de excepciones al trabajar con archivos, haciendo el código más seguro y robusto.