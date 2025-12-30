```
grep -E 'mario|lolo'   #Busca por expreciones regulares

Buscar algo en todos los ficheros de un directorio
grep patron /path/*

Si existen carpetas en el directorio de busqueda nos lanza un error pero se puede obviar con 
grep -s patron /path/*

grep -v patron /path/file   #Excluye el patron de la respuesta

Si lo convinamos con -E podemos escluir patrones mas complejos
grep -v -E 'mario|lolo' /etc/passwd
```