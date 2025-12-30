Se utiliza para la edición de stream

```
#Eliminar la 4 linea en input
$ sed '4d' input.txt > output.txt

Mostrar solo la linea 13
sed -n '13p' test.txt

Mostrar de la 1 a la 9
sed -n '1,9p' test.txt

Mostrar la 1 y la 9 
sed -n '1p;9p' test.txt

Cambiar la palabra hello por world del doc input y todo ponerlo en un doc output
sed ’s/hello/world/’ input.txt > output.txt

Para modifiar el mismo documento 
sed -i ’s/hello/world/’ input.txt

Mostrar cada 3 lineas
sed -n 'n;n;p' test.txt   ||  sed -n '3~3p'

Mostrar la ultima linea
sed -n '$p' test.txt

Susutituir cada 3 linea
seq 10 | sed 'n;n;s/./x/'

Ejecutar mas de una operacion elimina todo lo que empiece con food u sustitulle hello por world
sed '/^food/d ; s/hello/world/' test.txt > output.txt

Eliminar un rango de lineas
sed ’30,35d’ input.txt > output.txt

Cambiar todas las coincidencias
cat results.txt | sed 's/Adrian/Lolo/g'

Cambiar la segunda coincidencia por linea
cat results.txt | sed 's/Adrian/Lolo/2'
```