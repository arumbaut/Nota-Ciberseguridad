Pass next level: tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

Aqui nos conectamos pero nos sale solo una pantalla de Bienveida sin que estemos en un shell y no nos permite ejecutar comando alguno como si nos estuviera recibiendo un programa , hay que tener en cuenta que los programas en bash pueden recibir parametros y se este os lee 

Ej

```
ejemplo.sh
#!/bin/bash

echo "Estos son los valores de param $1 y param $2"     

Si hacemos un 
./ejemplo.sh Adrian Alonso

Nos muestra 
Adrian Alonso

Pero debemos tener en cuenta que cuando hacemos alucion al $0 este vale el valor del script que se ejecuta 
./ejemplo.sh
```

