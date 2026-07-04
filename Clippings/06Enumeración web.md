---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/728"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Enumeración web

---

Al realizar el escaneo de servicios, a menudo nos encontraremos con servidores web que se ejecutan en los puertos 80 y 443. Los servidores web alojan aplicaciones web (a veces más de 1) que a menudo proporcionan una superficie de ataque considerable y un objetivo de muy alto valor durante una prueba de penetración. Una enumeración web adecuada es fundamental, especialmente cuando una organización no expone muchos servicios o esos servicios están parcheados adecuadamente.

---

## Gobuster

Después de descubrir una aplicación web, siempre vale la pena verificar si podemos descubrir archivos o directorios ocultos en el servidor web que no estén destinados al acceso público. Podemos utilizar una herramienta como [ffuf](https://github.com/ffuf/ffuf) o [GoBuster](https://github.com/OJ/gobuster) para realizar esta enumeración de directorios. A veces encontraremos funcionalidades ocultas o páginas/directorios que exponen datos confidenciales que pueden aprovecharse para acceder a la aplicación web o incluso para la ejecución remota de código en el propio servidor web.

#### Directorio/Enumeración de archivos

GoBuster es una herramienta versátil que permite realizar operaciones brutas de DNS, vhost y directorios. La herramienta tiene funcionalidad adicional, como la enumeración de depósitos públicos de AWS S3. Para los fines de este módulo, nos interesan los modos de fuerza bruta de directorio (y archivo) especificados con el conmutador `dir`. Ejecutemos un escaneo simple usando el `dirb` `common.txt` lista de palabras.

```
shellsessionaalonso1190@htb[/htb]$ gobuster dir -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt

===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.10.121/
[+] Threads:        10
[+] Wordlist:       /usr/share/seclists/Discovery/Web-Content/common.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2020/12/11 21:47:25 Starting gobuster
===============================================================
/.hta (Status: 403)
/.htpasswd (Status: 403)
/.htaccess (Status: 403)
/index.php (Status: 200)
/server-status (Status: 403)
/wordpress (Status: 301)
===============================================================
2020/12/11 21:47:46 Finished
===============================================================
```

Un código de estado HTTP de `200` revela que la solicitud del recurso fue exitosa, mientras que un código de estado HTTP 403 indica que tenemos prohibido acceder al recurso. Un código de estado 301 indica que estamos siendo redirigidos, lo cual no es un caso de falla. Vale la pena familiarizarnos con los distintos códigos de estado HTTP que se pueden encontrar [aquí](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes). El `Web Requests` El módulo Academia también cubre los códigos de estado HTTP con mayor profundidad.

El escaneo se completó con éxito e identifica una instalación de WordPress en `/wordpress`. WordPress es el CMS (sistema de gestión de contenidos) más utilizado y tiene una enorme superficie de ataque potencial. En este caso, visitar `http://10.10.10.121/wordpress` en un navegador revela que WordPress todavía está en modo de configuración, lo que nos permitirá obtener ejecución remota de código (RCE) en el servidor.

![Pantalla de selección de idioma de WordPress con una lista de idiomas y un botón 'Continuar'.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/wordpress.png)

#### Enumeración de subdominios DNS

También puede haber recursos esenciales alojados en subdominios, como paneles de administración o aplicaciones con funcionalidad adicional que podrían explotarse. Podemos usar `GoBuster` enumerar los subdominios disponibles de un dominio determinado utilizando el `dns` bandera para especificar el modo DNS. Primero, clonemos SecLists GitHub [repo](https://github.com/danielmiessler/SecLists), que contiene muchas listas útiles para fuzzing y explotación:

#### Instalar SecLists

```
shellsessionaalonso1190@htb[/htb]$ git clone https://github.com/danielmiessler/SecLists
```
```
shellsessionaalonso1190@htb[/htb]$ sudo apt install seclists -y
```

A continuación, agregue un servidor DNS como 1.1.1.1 al `/etc/resolv.conf` archivo. Nos centraremos en el dominio `inlanefreight.com`, el sitio web de una empresa ficticia de transporte y logística.

```
shellsessionaalonso1190@htb[/htb]$ gobuster dns -d inlanefreight.com -w /usr/share/SecLists/Discovery/DNS/namelist.txt

===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Domain:     inlanefreight.com
[+] Threads:    10
[+] Timeout:    1s
[+] Wordlist:   /usr/share/SecLists/Discovery/DNS/namelist.txt
===============================================================
2020/12/17 23:08:55 Starting gobuster
===============================================================
Found: blog.inlanefreight.com
Found: customer.inlanefreight.com
Found: my.inlanefreight.com
Found: ns1.inlanefreight.com
Found: ns2.inlanefreight.com
Found: ns3.inlanefreight.com
===============================================================
2020/12/17 23:10:34 Finished
===============================================================
```

Este escaneo revela varios subdominios interesantes que podríamos examinar más a fondo. El [Atacar aplicaciones web con Ffuf](https://academy.hackthebox.com/module/details/54) El módulo ofrece más detalles sobre la enumeración y el fuzzing web.

---

## Consejos para la enumeración web

Repasemos algunos consejos adicionales de enumeración web que ayudarán a completar máquinas en HTB y en el mundo real.

#### Captura de banners / Encabezados de servidores web

En la última sección, analizamos el uso de banners con fines generales. Los encabezados del servidor web proporcionan una buena imagen de lo que está alojado en un servidor web. Pueden revelar el marco de aplicación específico en uso, las opciones de autenticación y si al servidor le faltan opciones de seguridad esenciales o ha sido mal configurado. Podemos usar `cURL` para recuperar información del encabezado del servidor desde la línea de comando. `cURL` es otra adición esencial a nuestro conjunto de herramientas de pruebas de penetración y se fomenta la familiaridad con sus numerosas opciones.

```
shellsessionaalonso1190@htb[/htb]$ curl -IL https://www.inlanefreight.com

HTTP/1.1 200 OK
Date: Fri, 18 Dec 2020 22:24:05 GMT
Server: Apache/2.4.29 (Ubuntu)
Link: <https://www.inlanefreight.com/index.php/wp-json/>; rel="https://api.w.org/"
Link: <https://www.inlanefreight.com/>; rel=shortlink
Content-Type: text/html; charset=UTF-8
```

Otra herramienta útil es [Testigo ocular](https://github.com/FortyNorthSecurity/EyeWitness), que se puede utilizar para tomar capturas de pantalla de aplicaciones web de destino, tomar huellas dactilares de ellas e identificar posibles credenciales predeterminadas.

#### Qué web

Podemos extraer la versión de servidores web, marcos de soporte y aplicaciones utilizando la herramienta de línea de comandos `whatweb`. Esta información puede ayudarnos a identificar las tecnologías en uso y comenzar a buscar vulnerabilidades potenciales.

```
shellsessionaalonso1190@htb[/htb]$ whatweb 10.10.10.121

http://10.10.10.121 [200 OK] Apache[2.4.41], Country[RESERVED][ZZ], Email[license@php.net], HTTPServer[Ubuntu Linux][Apache/2.4.41 (Ubuntu)], IP[10.10.10.121], Title[PHP 7.4.3 - phpinfo()]
```

`Whatweb` es una herramienta útil y contiene mucha funcionalidad para automatizar la enumeración de aplicaciones web en una red.

```
shellsessionaalonso1190@htb[/htb]$ whatweb --no-errors 10.10.10.0/24

http://10.10.10.11 [200 OK] Country[RESERVED][ZZ], HTTPServer[nginx/1.14.1], IP[10.10.10.11], PoweredBy[Red,nginx], Title[Test Page for the Nginx HTTP Server on Red Hat Enterprise Linux], nginx[1.14.1]
http://10.10.10.100 [200 OK] Apache[2.4.41], Country[RESERVED][ZZ], HTTPServer[Ubuntu Linux][Apache/2.4.41 (Ubuntu)], IP[10.10.10.100], Title[File Sharing Service]
http://10.10.10.121 [200 OK] Apache[2.4.41], Country[RESERVED][ZZ], Email[license@php.net], HTTPServer[Ubuntu Linux][Apache/2.4.41 (Ubuntu)], IP[10.10.10.121], Title[PHP 7.4.3 - phpinfo()]
http://10.10.10.247 [200 OK] Bootstrap, Country[RESERVED][ZZ], Email[contact@cross-fit.htb], Frame, HTML5, HTTPServer[OpenBSD httpd], IP[10.10.10.247], JQuery[3.3.1], PHP[7.4.12], Script, Title[Fine Wines], X-Powered-By[PHP/7.4.12], X-UA-Compatible[ie=edge]
```

#### Certificación

Los certificados SSL/TLS son otra fuente de información potencialmente valiosa si se utiliza HTTPS. Navegando a `https://10.10.10.121/` y al ver el certificado se revelan los detalles a continuación, incluida la dirección de correo electrónico y el nombre de la empresa. Estos podrían usarse potencialmente para realizar un ataque de phishing si esto está dentro del alcance de una evaluación.

![Detalles del certificado de Megabank Limited, incluida información sobre el tema y el emisor con país, estado, localidad, organización y dirección de correo electrónico.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/cert.png)

#### Robots.txt

Es común que los sitios web contengan un `robots.txt` archivo, cuyo propósito es indicar a los rastreadores web de motores de búsqueda como Googlebot a qué recursos se puede y no se puede acceder para indexarlos. El `robots.txt` El archivo puede proporcionar información valiosa, como la ubicación de archivos privados y páginas de administración. En este caso, vemos que el `robots.txt` El archivo contiene dos entradas no permitidas.

![El archivo Robots.txt no permite el acceso a /private y /uploaded_files para todos los agentes de usuario.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/robots.png)

Navegando hacia `http://10.10.10.121/private` En un navegador se revela una página de inicio de sesión de administrador HTB.

![Formulario de inicio de sesión con campos para nombre de usuario y contraseña, y un botón de inicio de sesión.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/academy.png)

#### Código fuente

También vale la pena verificar el código fuente de cualquier página web que encontremos. Podemos golpear `[CTRL + U]` para abrir la ventana del código fuente en un navegador. Este ejemplo revela un comentario de desarrollador que contiene credenciales para una cuenta de prueba, que podría usarse para iniciar sesión en el sitio web.

![Fragmento HTML con credenciales de cuenta de prueba, metaetiquetas y título de inicio de sesión de administrador.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/source.png)

## Conéctese a HTB

Habilite soluciones paso a paso

PRO

- ## Pregunta 1
	+1
	+20
	---