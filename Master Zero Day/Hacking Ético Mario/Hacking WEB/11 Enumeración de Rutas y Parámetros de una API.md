- Tags : #apis #enumeration #recursos #recursos_hackerlabs #js_ofuscado #unpacker_js

**Recurso**: Maquina ofuspingu thehackerlabs.com

```bash
gobuster dirb -u http://url:pot/ -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-2.3-medium.txt -x php,py,html,js,txt

Obtenido el directorio donde esta la api haremos un fucer para identificar los parametros y sus valores
Carpeta que contiene la API /api

wfuzz -c --hh=33 -u http://url:pot/api?FUZZ -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-2.3-medium.txt

Encontramos el parametro token 

```

Los códigos de JS ofuscados en la pagina también deben revisarse para ver si obtenemos alguna información

Buscamos js unpacker en el navegador y probamos algunos des-ofuscadores online
**Recurso**: [https://matthewfl.com/unPacker.html](https://matthewfl.com/unPacker.html)

Dentro de el código de js ofuscado encontramos el valor de el token y hacemos una petición al sitio con el parametro y su valor