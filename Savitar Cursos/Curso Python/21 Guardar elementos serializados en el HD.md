
```
impot pickle

#leer de un archivo serializado 

with open("archivo.pkl","rb") as f:
	contenido= pickle.load(f)

#Escribir en un archivo
notas=[
	{"titulo":"Aseo","info":"hssfkhsdkfhsldfhsldkhf"},
	{"titulo":"Cocina","info":"hssfkhsdkfhsldfhsldkhf"}
] 
with open("archivo.pkl","wb") as f:
	pickle.dump(notas,f)

```


Limpiar consola con la liberia os 
```
import os
os.system('cls',if os.name == 'nt' else 'clear')
```