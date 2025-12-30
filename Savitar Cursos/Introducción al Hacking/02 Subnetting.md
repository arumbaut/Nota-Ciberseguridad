```
#!/bin/bash

read -p "Introducir el nombre del archivo a buscar : " nombre

resultado="$(find / -type f -iname "$nombre*" 2>/dev/null | awk '{print $0}')"

echo $resultado
```