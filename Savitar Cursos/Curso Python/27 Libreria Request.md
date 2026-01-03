Recurso para practicar con la libreria requests
https://httpbin.org/

```
import requests

Peticion get 

response=request.get(url)

Pasandole parametros
values={'key1':'value1','key2':'value2'}
request.get(url,params=values)

Post
request.post(url)

Pasando parametros por pos
payloads={'key1':'value1','key2':'value2'}
request.post(url,data=payloads)

Pasando Cabeceras
payloads={'key1':'value1','key2':'value2'}
headers={'User-Agent':'my-app/1.0.0'}
request.post(url, data=payloads, headers=headers)

Pasar TimeOut para manejar la espera de una peticion

response= request.get(url,timeoust=1)
Para mostrar un error si no cumple con el margen de tiempo
response.raise_for_status()   

Lanzmiento de exepciones para manejar los errores en las peticiones
try:
	response= request.get(url,timeoust=1)
	response.raise_for_status()   
except requests.Timeout:
	algo
except requests.HTTPError as htt_err:
	print(http_err)
except requests.RequestException as err:
	print(err)
else: 
	print('Todo genial')
	

Status code de la respuesta
response.status_code

Respuesta
response.text


Url
response.url

Headers
response.request.headers

Interpretar las respuestas JSON en formato de python
response= request.get(url,timeoust=1)
data=response.json()  #Genera un diccionario para trabajar con el desde python

#Ejemplo
data['Headers']['User-Agent']
 
```

Autenticacion

```
response= requests.get('https://httpbin.org/basic-auth/adrian/lolo',auth=('adrian','lolo'))

response.status_code
```

Modificacionde Cookies
```
cookies=dict(cookies_are='working')
response= requests.get('https://httpbin.org/cookies',cookies=cookies)
```

Subir recursos
```
url='https://httpbin.org/post'
my_file={'archivo': opene('example.txt','r')}
response= requests.post(url,files=my_file)

```

Cookies de Session Arrastrar las Cookies de session
```
from requests import Request, Session
session=requests.Session()
url='https://httpbin.org/cookies'
set_cookies_url='https://httpbin.org/cookies/mi_cookie/1234'
response= session.get(set_cookies_url)
response== session.get(url)
```

Preparar una solicitud antes de enviarla
```
from requests import Request, Session
session=Session()
url='https://httpbin.org/cookies'

headers={'Custom-Haeder':'mi-custom-header'}
req= Request('GET', url, headers=headers)
prepped= req.prepare()

prepped.headers['Custom-Header']='changed-header'
response=session.send(prepped)

```

Historico de url
```
impedir redireccion
r = request.get(url,allow_redirects=false)

historico
r.history   #Es un iterable por lo que 

for req in r.history:
	print(f"{req.url}  {req.status_code} ")
```

Arrastras seesiones en un contexto with
```
#!/usr/bin/env python3

import requests

# https://httpbin.org/basic-auth/foo/bar

with requests.Session() as session:
    session.auth = ('foo', 'bar') #Pasar los valores de autenticacion
    response1 = session.get('https://httpbin.org/basic-auth/foo/bar')
    print(response1.text)

    response2 = session.get('https://httpbin.org/basic-auth/foo/bar')
    print(response2.text)
```


‘**requests**‘ es una biblioteca de Python que simplifica enormemente el proceso de enviar solicitudes HTTP. Está diseñada para ser más fácil de usar que las opciones incorporadas en Python, como ‘**urllib**‘, proporcionando una API más amigable.

**Características Principales**

- **Simplicidad y Facilidad de Uso**: Con requests, enviar solicitudes GET, POST, PUT, DELETE, entre otras, se puede realizar en pocas líneas de código. Su sintaxis es clara y concisa.
- **Gestión de Parámetros URL**: Permite manejar parámetros de consulta y cuerpos de solicitud con facilidad, automatizando la codificación de URL.
- **Manejo de Respuestas**: ‘**requests**‘ facilita la interpretación de respuestas HTTP, proporcionando un objeto de respuesta que incluye el contenido, el estado, los encabezados, y más.
- **Soporte para Autenticaciones**: Ofrece soporte integrado para diferentes formas de autenticación, incluyendo autenticación básica, digest, y OAuth.
- **Manejo de Sesiones y Cookies**: Permite mantener sesiones y gestionar cookies, lo cual es útil para interactuar con sitios web que requieren autenticación o mantienen estado.
- **Soporte para SSL**: ‘**requests**‘ maneja SSL (Secure Sockets Layer) y TLS (Transport Layer Security), permitiendo realizar solicitudes seguras a sitios HTTPS.
- **Manejo de Excepciones y Errores**: Proporciona métodos para manejar y reportar errores de red y HTTP de manera efectiva.

**Uso Práctico**

La biblioteca se utiliza ampliamente para interactuar con APIs RESTful, automatizar interacciones con sitios web, y en tareas de scraping web. Sus capacidades para manejar solicitudes complejas y sus características de seguridad la hacen ideal para una amplia gama de aplicaciones, desde scripts simples hasta sistemas empresariales complejos.