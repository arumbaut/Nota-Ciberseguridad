- Tags : #apis #potsman #recursos_github #ffuf 

**Actualización 24/05/2023**: Si a la hora de desplegar el laboratorio con Docker, os encontráis con problemas y alguno de los contenedores que se despliegan véis que causan error, probad a desplegar como alternativa el laboratorio de desarrollo.

Primeramente instalad la última versión de ‘**docker-compose**‘ y una vez hecho, ejecutad los siguientes comandos:

- **curl -o docker-compose.yml https://raw.githubusercontent.com/OWASP/crAPI/develop/deploy/docker/docker-compose.yml**
- **VERSION=develop docker-compose pull**
- **VERSION=develop docker-compose -f docker-compose.yml –compatibility up -d**

En caso de que veáis que tras desplegar el laboratorio, siguen habiendo errores en el despliegue de ciertos contenedores, probad a hacer un ‘**docker rm $(docker ps -a -q) –force**‘ y aplicad el último comando de los 3 mencionados anteriormente para volver a desplegar los contenedores. Llegará un momento en el que todos serán desplegados sin ningún problema.

Por otro lado, si de pronto véis que el comando ‘**docker rm $(docker ps -a -q) –force**‘ os da algún problema, esperad unos segundos y volved a probar el comando hasta que veáis que todos los contenedores han sido eliminados.

Cuando hablamos del abuso de APIs, a lo que nos referimos es a la explotación de vulnerabilidades en las interfaces de programación de aplicaciones (**APIs**) que se utilizan para permitir la comunicación y el intercambio de datos entre diferentes aplicaciones y servicios en una red.

Un ejemplo sencillo de API podría ser la integración de Google Maps en una aplicación de transporte. Imagina que una aplicación de transporte necesita mostrar el mapa y la ruta a seguir para que los usuarios puedan ver la ubicación del vehículo y el camino que se va a seguir para llegar a su destino. En lugar de crear su propio mapa, la aplicación podría utilizar la API de Google Maps para mostrar el mapa en su aplicación.

En este ejemplo, la API de Google Maps proporciona una serie de funciones y protocolos que permiten a la aplicación de transporte comunicarse con los servidores de Google y acceder a los datos necesarios para mostrar el mapa y la ruta. La API de Google Maps también maneja la complejidad de mostrar el mapa y la ruta en diferentes dispositivos y navegadores, lo que permite a la aplicación de transporte centrarse en su funcionalidad principal.

Adicionalmente, una de las utilidades que vemos en esta clase es **Postman**. Postman es una herramienta muy popular utilizada para probar y depurar APIs. Con Postman, los desarrolladores pueden enviar solicitudes a diferentes endpoints y ver las respuestas para verificar que la API está funcionando correctamente. Sin embargo, los atacantes también pueden utilizar Postman para explorar los endpoints de una API en busca de vulnerabilidades y debilidades de seguridad.

Algunos endpoints de una API pueden aceptar diferentes métodos de solicitud, como GET, POST, PUT, DELETE, etc. Los atacantes pueden utilizar herramientas de fuzzing para enviar una gran cantidad de solicitudes a un endpoint en busca de vulnerabilidades. Por ejemplo, un atacante podría enviar solicitudes GET a un endpoint para enumerar todos los recursos disponibles, o enviar solicitudes POST para agregar o modificar datos.

Algunas de las vulnerabilidades comunes que se pueden explotar a través del abuso de APIs incluyen:

- **Inyección de SQL**: los atacantes pueden enviar datos maliciosos en las solicitudes para intentar inyectar código SQL en la base de datos subyacente.
- **Falsificación de solicitudes entre sitios (CSRF)**: los atacantes pueden enviar solicitudes maliciosas a una API en nombre de un usuario autenticado para realizar acciones no autorizadas.
- **Exposición de información confidencial**: los atacantes pueden explorar los endpoints de una API para obtener información confidencial, como claves de API, contraseñas y nombres de usuario.

Para evitar el abuso de APIs, los desarrolladores deben asegurarse de que la API esté diseñada de manera segura y que se validen y autentiquen adecuadamente todas las solicitudes entrantes. También es importante utilizar cifrado y autenticación fuertes para proteger los datos que se transmiten a través de la API.

Los desarrolladores pueden utilizar herramientas como Postman para probar la API y detectar posibles vulnerabilidades antes de que sean explotadas por los atacantes.

A continuación, se proporciona el enlace al proyecto de Github que utilizamos para desplegar con Docker el laboratorio vulnerable donde poder practicar la enumeración de APIs:

- **crAPI**: [https://github.com/OWASP/crAPI](https://github.com/OWASP/crAPI)

```bash
ffuf -u http//localhost:8888/identity/api/auth/v3/check-opt -w /usr/share/seclists/Fuzzing/4-digits-0000-9999.txt -X POST -d {"email":"savitar@hack4you.com", "opt":"FUZZ", "password":"Newpass1234"} -H "Content-Type: application/json" -p 1 -mc 200

--Historial--
-X  POST #Indica el metodo http
-u       #Indica la url
-w       #Indica el diccionario a utilizar
-d       #Indica la data a enviar por parametro en peticiones POST
-p       #Indica intervalo de tiempo entre peticiones
-mc      #Match HTTP status codes, or "all" for everything. (default: 200-299,301,302,307,401,403,405,500)
```

Hacer fuzz para determinar los métodos disponibles en la api , utilizaremos otro diccionario de la seclist.  Es recomendable probar si una petición se puede realizar por diferentes métodos e incluso si la petición a la api tiene habilitada otras versiones activas, en los campos de valor introducir numeros negativos para ver que ocurre a nivel de aplicacion
```bash
locate \*method\* | grep -i seclist
/usr/share/seclists/Fuzzing/http-request-methods.txt
/usr/share/seclists/Fuzzing/php-magic-methods.txt

ffuf -u http//localhost:8888/workshop/api/shop/products -w /usr/share/seclists/Fuzzing/http-request-methods.txt -X FUZZ -p 1 -mc 200,401
```