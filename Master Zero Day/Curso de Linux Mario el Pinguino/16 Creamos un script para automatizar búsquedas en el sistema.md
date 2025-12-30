
```
#!/bin/bash

read "Introducir el nombre del archivo a buscar" nombre

find / -iname $nombre 2>/dev/null
```