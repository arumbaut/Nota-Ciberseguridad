```
#!/bin/bash

for archivo in *
do
    extension=$(echo "$archivo" | awk -F '.' '{print $NF}')

    case "$extension" in
        txt)
            zip -r documentos.zip $archivo >/dev/null
            ;;
    esac
done

mkdir -p servidor/ && mv documentos.zip servidor/

ip=$(hostname -I)

echo "Inserte la $ip desde otro navegador"

cd servidor/ && python3 -m http.server 80
```