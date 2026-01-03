```
import re
texto = "Mi gato esta en el tejado y mi otro gato en el jardin"

matches=re.findall("gato",text)

Patron digito de 2 posiciones d{2} , de n dig d{n}
en las regexp se deben escapar los / con \/ 
matches=re.findall("\d{2}\/d{2}\/d{4}",text)

Patron para secciones especificas caracteres los separa en tuplas los parentesis ,alfanumericos w+
matches=re.findall("(\w+)@(\w+\.\w{2,})",text)


Aplicar sustituciones sub
new_text=re.sub("sustituir","sustituto",texto)

Split de cadena a partir de un patron
new_text=re.split(',',texto)


Buscar por patrones 
patron="\b(\d{2}\/\d}{2}\/\d{4})\b"

for match in ri.finditer(patron,text)
	print(f"{match.group(0)}")

```


Validador de correo
```
def validar_correo(correo):
	patron="\b[A-za-z0-9._+-]+@[A-za-z0-9]+\.[A-za-z]{2,}\b"
	if re.findall(patron,correo):
		return True
	else:
		return False	
	
```



Aquí hay varios aspectos importantes de esta librería:

- **Funciones Básicas**: ‘**re**‘ incluye funciones como ‘**search**‘ (para buscar un patrón dentro de una cadena), ‘**match**‘ (para verificar si una cadena comienza con un patrón específico), ‘**findall**‘ (para encontrar todas las ocurrencias de un patrón), y ‘**sub**‘ (para reemplazar partes de una cadena que coinciden con un patrón).
- **Compilación de Patrones**: Permite compilar expresiones regulares en objetos de patrón, lo que puede mejorar el rendimiento cuando se usan repetidamente.
- **Grupos y Captura**: Ofrece la capacidad de definir grupos dentro de patrones de expresiones regulares, lo que facilita extraer partes específicas de una cadena que coinciden con subpatrones.
- **Flags**: Soporta modificadores que alteran la forma en que las expresiones regulares son interpretadas y coincididas, como ignorar mayúsculas y minúsculas o permitir el modo multilínea.
- **Patrones Complejos**: Permite la creación de patrones complejos utilizando una variedad de símbolos y secuencias especiales, como cuantificadores, aserciones y clases de caracteres.
- **Aplicaciones Prácticas**: Las expresiones regulares son extremadamente útiles en tareas como la validación de formatos (por ejemplo, direcciones de correo electrónico), el análisis de registros (logs), el procesamiento de lenguaje natural, y la limpieza y preparación de datos.
- **Curva de Aprendizaje**: Aunque potentes, las expresiones regulares pueden ser complejas y requieren una curva de aprendizaje. Sin embargo, una vez dominadas, se convierten en una herramienta invaluable en el arsenal de cualquier programador.