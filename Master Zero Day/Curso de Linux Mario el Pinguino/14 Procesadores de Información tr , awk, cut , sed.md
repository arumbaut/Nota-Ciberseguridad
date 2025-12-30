
tr - > para sustituir caracteres en concreto, uno por uno no se puede sustituir un carácter por varios
```
Bien
echo "Hola que tal" | tr 'a' '-'
echo "Hola que tal" | tr 'Ho' '--'

Error
echo "Hola que tal" | tr 'a' '--'
```

AWK - > Procesador de textos para filtrar la info
```
Sintaxis
Referencia a la columna 1
awk '{print $1}' 

Referir al ultimo elemento
awk '{print $NF}'

Adicionar algo entre las columnas seleccionadas
awk '{print $1 "-->" $2}'

Establecer delimitador
awk -F ',' {print $1}'

```

Cut --> Para manipular caracteres de una cadena de texto

```
Referirme a la 1 letra
echo "Hola que tal" | cut -c 1

Referir a las 2 primeras
echo "Hola que tal" | cut -c 1,2

Solo la 3
echo "Hola que tal" | cut -c 3

Un rango 
echo "Hola que tal" | cut -c 1-5

Establecer deliminitador y mostrar por columnas
echo "Hola que tal" | cut -d ',' -f 1


```

Sed --> Herramienta para poder editar texto en linux

```
sed 's/palabra/palabrasustituta/'  1 coincidencia

sed 's/palabra/palabrasustituta/g'  Todas las coincidencia

set -i 's/$/ El gato es feliz/' lolo.txt Agrega el gato es feliz al final de cada linea y modifica lolo.txt
```