```
#!/bin/bash


if [ $# -ne 2 ]; then
    echo "Uso : <archivo> <wordlist>"
fi

archivo=$1
wordlist=$2

case "$archivo" in
    *.kdbx)
        keepass2john "$archivo" > hash
        ;;
    *.zip)
        zip2john "$archivo" > hash
        ;;
    *)
        echo "Archivo no compatible, solo .zip y .kdbx"
        exit 1
        ;;
esac

john --wordlist="$wordlist" hash

john --show hash

rm hash
```