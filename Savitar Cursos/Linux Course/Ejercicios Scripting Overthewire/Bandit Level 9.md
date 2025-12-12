Cuando un archivo no es legible se recomienda lanzarle un string .El comando **strings** de Linux permite ver los caracteres legibles para humanos dentro de cualquier archivo.

Pass next level: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
strings data.txt | grep -E "*=====" | tail -n 1 | awk 'NF{print $NF}'
```