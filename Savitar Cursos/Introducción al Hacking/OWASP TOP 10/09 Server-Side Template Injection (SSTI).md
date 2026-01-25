- Tags : #recursos_github #ssti #payloads #payloads_link
El **Server-Side Template Injection** (**SSTI**) es una vulnerabilidad de seguridad en la que un atacante puede inyectar código malicioso en una **plantilla** de servidor.

Las plantillas de servidor son archivos que contienen código que se utiliza para generar **contenido dinámico** en una aplicación web. Los atacantes pueden aprovechar una vulnerabilidad de SSTI para inyectar código malicioso en una plantilla de servidor, lo que les permite ejecutar comandos en el servidor y obtener acceso no autorizado tanto a la aplicación web como a posibles datos sensibles.

Por ejemplo, imagina que una aplicación web utiliza plantillas de servidor para generar correos electrónicos personalizados. Un atacante podría aprovechar una vulnerabilidad de **SSTI** para inyectar código malicioso en la plantilla de correo electrónico, lo que permitiría al atacante ejecutar comandos en el servidor y obtener acceso no autorizado a los datos sensibles de la aplicación web.

En un caso práctico, los atacantes pueden detectar si una aplicación Flask está en uso, por ejemplo, utilizando herramientas como **WhatWeb**. Si un atacante detecta que una aplicación **Flask** está en uso, puede intentar explotar una vulnerabilidad de **SSTI**, ya que Flask utiliza el motor de plantillas **Jinja2**, que es vulnerable a este tipo de ataque.

Para los atacantes, detectar una aplicación Flask o Python puede ser un primer paso en el proceso de intentar explotar una vulnerabilidad de SSTI. Sin embargo, los atacantes también pueden intentar identificar vulnerabilidades de SSTI en otras aplicaciones web que utilicen diferentes frameworks de plantillas, como Django, Ruby on Rails, entre otros.

Para prevenir los ataques de SSTI, los desarrolladores de aplicaciones web deben validar y filtrar adecuadamente la entrada del usuario y utilizar herramientas y frameworks de plantillas seguros que implementen medidas de seguridad para prevenir la inyección de código malicioso.

**Recurso de payloads** : [https://github.com/swisskyrepo/PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
**Infayer web site**  : [https://infayer.com/archivos/803](https://infayer.com/archivos/803)

Escenario nos crearemos un contenedor en docker con flask para ejecutar el ataque SSTI

```bash
docker run -p 8089:8089 -d filipkarc/ssti-flask-hacking-playground
```

Cuando estamos testeando un sitio y vemos que utiliza python con flask esta es un buen punto de partida en caso de que podamos tener control sore algún input y veamos reflejada en la salida nuestra entrada


```
{{7*7}} #Lo ponemos en una entrada y vemos si lo refleja el resultado 

Utilizamos el recurso de https://github.com/swisskyrepo/PayloadsAllTheThings
para inyectar diferentes payload en el campo e ir viendo cual nos funciona
```