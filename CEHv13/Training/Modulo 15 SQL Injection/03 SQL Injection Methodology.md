La metodología de inyección SQL consta de los siguientes pasos:

**▪ Recopilación de información y detección de vulnerabilidades de inyección SQL**
**▪ Lanzamiento de ataques de inyección SQL**
**▪ Compromiso de toda la red objetivo (inyección SQL avanzada)**

**Information Gathering**

Information can be gathered in the following steps:

1. Check if the web application connects to a database server to access some data
2.  List all input fields and hidden fields, and post requests whose values could be used for crafting an SQL query
3. Attempt to inject code into the input fields to generate an error
4. Try to insert a string value where a number is expected in the input field
5. Use the UNION operator to combine the result sets of two or more SELECT statements
6. Check the detailed error messages to gain information to execute SQL injection

**Identifying Data Entry Paths**

 tools to find input gates for SQL injection.

**▪ Tamper Dev Source: https://chromewebstore.google.com**
**▪ Burp Suite Source: https://www.portswigger.net**

**Extracting Information through Error Messages**

Según el tipo de información obtenida del mensaje de error, el atacante elige una técnica de inyección SQL para explotar la vulnerabilidad en la aplicación. Los atacantes pueden obtener información de los mensajes de error mediante los siguientes métodos:

**▪ Parameter Tampering**
==Un atacante puede manipular las solicitudes HTTP GET y POST para generar errores. Los mensajes de error obtenidos mediante esta técnica pueden proporcionar al atacante información como el nombre del servidor de base de datos, la estructura del directorio y las funciones utilizadas en la consulta SQL. Los parámetros pueden **manipularse****(tampered )** directamente desde la barra de direcciones o utilizando proxies==.

Por ejemplo

http://certifiedhacker.com/download.php?id=car http://certifiedhacker.com/download.php?id=horse http://certifiedhacker.com/download.php?id=book

**▪ Grouping Error**

El comando HAVING permite refinar una consulta basada en los campos que han sido agrupados utilizando GROUP BY. Cuando se utiliza incorrectamente, es decir, cuando se especifica una columna que no ha sido incluida en el GROUP BY, el servidor SQL generará un mensaje de error.

**▪ Type Mismatch**

Consiste en **intentar insertar valores de un tipo de dato incorrecto** (por ejemplo, una cadena de texto en un campo numérico). Al hacerlo, la base de datos generará un mensaje de error que **puede revelar información útil** sobre la estructura de los campos y el tipo de datos esperado.

**▪ Blind Injection**

Usa retrasos de tiempo o firmas de error para determinar o extraer información.
For example:
**'; if condition waitfor delay '0:0:5' --';**

**union select if( condition , benchmark (100000, sha1('test')), 'false' ),1,1,1,1;**

**Nota: Si las aplicaciones no proporcionan mensajes de error detallados y devuelven simplemente un '500 Server Error' o una página de error personalizada, entonces se deben intentar técnicas de inyección SQL a ciegas (blind injection).**