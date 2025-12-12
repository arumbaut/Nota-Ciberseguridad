Pass next level: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
Mas de tareas cron

En este caso la tarea con que ejecuta el usuario bandit23 es la siguient
```
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

Lo que hace es crear un archivo temporal al cual le introduce la password lo interesnte el la manera como genera el nimbre del archivo creandolo en hash md5 

mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

por lo que podemos replicar este comando poniendole como parametro el username bandit23

bandit22@bandit:/etc/cron.d$ echo "I am user bandit23" | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349

Posteriormente leemos este archivo y obtenemos la pass
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga

```
