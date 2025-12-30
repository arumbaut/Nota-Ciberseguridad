Bucle for

```
for i in {1..50};do
    codigo a ejecutar
done    

for i in seq 50;do
    codigo a ejecutar
done  

Recorrer lo que hay en una ruta
 for i in "/home/alexandross/Adrian/Estudio/Cursos Hack/Savitar Academy/Scripts/"*;do 
     echo "$i";
 done
 
Recorrer lo que hay enn el directorio actual
 for i in *;do 
     echo "$i";
 done
 
Leer las lineas de un fichero
for linea in $(cat "recorrer_lineas.txt"); do 
   echo "En esta vuelta, la variable linea vale $linea" 
done
```

Wile

```
count=1 
while [ $count -le 5 ] 2>/dev/null; do 
   echo "Count is $count" 
   ((count++)) 
done

Recorrer lineas dentro de un fichero 
while read url ; do 
   resp=$(cur -s -0 /dev/null -w "%{http_code}" "$url")
   echo "Codigo de estado de "$url" es "$resp" "  
done < fichero


```

Until
```
# Until loop example 
count=1 
until [ $count -gt 5 ]; do 
   echo "Count is $count" 
   ((count++)) 
done
```