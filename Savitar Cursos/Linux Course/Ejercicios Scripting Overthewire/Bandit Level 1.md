Pass next level: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
sshpass -p 'ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If' ssh bandit1@bandit.labs.overthewire.org -p 2220
```

La idea es leer un fichero de nombre   -  esto nos da problema si hacemos un cat -, por lo que pondremos su ruta absoluta.
```
cat /home/bandit1/-

cat ./- 

cat $(pwd)/-  
```

Otras variantes
```
grep -r "\w" 2>/dev/null | tail -n 1 | awk '{print $2}' FS=":"

grep -r "\w" 2>/dev/null | tail -n 1 | cut -d ':' -f 2

grep -r "\w" 2>/dev/null | tail -n 1 | tr ':' ' ' |awk '{print $2}'

grep -r "\w" 2>/dev/null | tail -n 1 | awk 'NF{print $NF}  NF referencia al ultimo argumento de la linea
 ```