**▪ In-band SQL Injection:**   Un atacante utiliza el mismo canal de comunicación tanto para llevar a cabo el ataque como para obtener los resultados. Las variantes más utilizadas de la inyección SQL in-band son la inyección SQL basada en errores (**error-based SQL injection)** y la **inyección SQL mediante UNION (UNION SQL injection).** 

**▪ Blind/Inferential SQL Injection:** El atacante no recibe mensajes de error del sistema para guiar su ataque. En su lugar, envía consultas SQL maliciosas al servidor de base de datos y observa el comportamiento de la aplicación para inferir información.

**▪ Out-of-Band SQL Injection:** Los atacantes utilizan canales de comunicación distintos al principal (como funcionalidades de correo electrónico del sistema de bases de datos o funciones de escritura y carga de archivos) para ejecutar el ataque y obtener los resultados.

 **Ataques In-Band SQL Injection **
 
** Error-based SQL Injection**

 Un atacante inserta intencionalmente entradas incorrectas en una aplicación, lo que provoca que se devuelvan errores a nivel de base de datos.  El atacante analiza los mensajes de error resultantes para identificar vulnerabilidades de inyección SQL en la aplicación

**System Stored Procedure**
Un atacante puede aprovechar las entradas maliciosas para ejecutar las consultas SQL maliciosas dentro del procedimiento almacenado

**Illegal/Logically Incorrect Query** **:**
Un atacante puede obtener información inyectando solicitudes ilegales/lógicamente incorrectas, como parámetros inyectables, tipos de datos, nombres de tablas, etc. En este ataque de inyección SQL, un atacante envía intencionadamente una consulta incorrecta a la base de datos para generar un mensaje de error que puede ser útil para realizar ataques adicionales.

Ejemplo
**SELECT * FROM Users WHERE UserName = 'Bob"' AND password =**

**UNION SQL Injection**

La instrucción **“UNION SELECT”** devuelve la unión del conjunto de datos previsto con el conjunto de datos objetivo. En una inyección SQL mediante UNION, un atacante utiliza una cláusula **UNION** para anexar una consulta maliciosa a la consulta original solicitada, como se muestra en el siguiente ejemplo

**SELECT Name, Phone, Address FROM Users WHERE Id=1 UNION ALL SELECT creditCardNumber,1,1 FROM CreditCardTable**

**▪ Tautology**
Un atacante utiliza una cláusula condicional OR de manera que la condición de la cláusula WHERE siempre sea verdadera. Este tipo de ataque puede usarse para eludir la autenticación de usuarios. Por ejemplo:

**SELECT * FROM users WHERE name = ‘’ OR ‘1’=‘1’;**

**End-of-Line Comment**
 Los comentarios en una línea de código suelen estar representados por (--), y son ignorados por la consulta. Un atacante se aprovecha de esta característica de los comentarios escribiendo una línea de código que termina en un comentario. La base de datos ejecutará el código hasta llegar a la parte comentada,

**SELECT * FROM members WHERE username = 'admin'--' AND password = 'password'**

**In-line Comments**
Un ataque de inyección SQL integrando múltiples entradas vulnerables en una sola consulta mediante el uso de comentarios en línea. Este tipo de inyección permite al atacante eludir listas negras, eliminar espacios, ofuscar código y determinar versiones de bases de datos.

Por ejemplo:
**INSERT INTO Users (UserName, isAdmin, Password) VALUES ('".$username."', 0, '".$password."')

**Piggybacked Query**
Este tipo de inyección se realiza generalmente en consultas SQL por lotes. La consulta original permanece sin modificar, y la consulta del atacante se acopla a esta. Gracias a este acoplamiento, el sistema de gestión de bases de datos (DBMS) recibe múltiples consultas SQL. Los atacantes utilizan un punto y coma (;) como delimitador de consultas para separar las instrucciones.Este tipo de ataque también se conoce como stacked queries attack. El objetivo del atacante puede ser extraer, agregar, modificar o eliminar datos, ejecutar comandos remotos o realizar un ataque de denegación de servicio (DoS).


** Ataques Blind/Inferential SQL Injection**

 **Blind SQL Injection: Time-based SQL Injection**
La inyección SQL basada en tiempo (a veces llamada inyección SQL de retraso en el tiempo) evalúa el retraso temporal que ocurre en respuesta a consultas de verdadero o falso enviadas a la base de datos. Una declaración WAITFOR detiene el servidor SQL durante un tiempo específico. 

**Blind SQL Injection: Boolean Exploitation Boolean**
El atacante utiliza un conjunto de operaciones booleanas para extraer información sobre las tablas de la base de datos.  Si la aplicación no devuelve ningún mensaje de error predeterminado, el atacante intenta usar operaciones booleanas contra la aplicación. 
Nota: Uso de AND 

Ejemplo 
SELECT Name, Price, Description FROM ITEM_DATA WHERE ITEM_ID = 67 AND 1 = 2

**Blind SQL Injection: Heavy Query**
Una consulta pesada recupera una gran cantidad de datos y tomará mucho tiempo para ejecutarse en el motor de base de datos. Los atacantes generan consultas pesadas utilizando múltiples uniones en las tablas del sistema, porque las consultas sobre tablas del sistema suelen tardar más tiempo en ejecutarse.

 