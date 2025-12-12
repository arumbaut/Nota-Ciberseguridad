Pass next level: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

```
find . -type f -readable      #Busca archivos que se pueden leer

find . -type f -executable    #Busca archivos que se puedan ejecutar

!  Simpolo de negacion
find . -type f ! -executable    #Busca archivos que no se puedan ejecutar

find . -type f -size 1033c -readable ! -executable   

Para mayor que el tamaño  
find . -type f -size +1033c -readable ! -executable 

Menor que 
find . -type f -size -1033c -readable ! -executable 
```

