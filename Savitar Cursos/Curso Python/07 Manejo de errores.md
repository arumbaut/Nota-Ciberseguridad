```
try:

except:

try:
 #num= 5/0  Ejemplo 1
 #num= "hola"/3   Ejemplo2
except ZeroDivisionError:
	print("No se puede dividir un numero entre 0") 
execpt TypeError:
	print("Solo es posible dividir numeros ")

else:
	print(f"El valor es {num}")

finaly:   #Siempre se ejecuta esto
	print("Siempre me ejecuto")		
	

```

Lanzar una excepcion
```
if x<0:
	rice Exception("no se pueden utilizar numeros negativos")
```

Modulo pwn para mostrar errores
Install modulo de pwn
```
sudo apt install python3-pwntools
```

```
from pwn import log

try:

except:

try:
 #num= 5/0  Ejemplo 1
 #num= "hola"/3   Ejemplo2
except ZeroDivisionError:
	print("No se puede dividir un numero entre 0") 
execpt TypeError:
	log.failure("Solo es posible dividir numeros ")
```