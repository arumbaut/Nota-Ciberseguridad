- Tags : #veracrypt #veracrypt_bloqueado
Cuando se queda bloqudo por un proceso y no deja despontar

```bash

 mount | grep veracryp  #Obtenemos deonde se monto
 sudo lsof +D /media/veracrypt3 #Nos da quien esta utilizando el recurso
 sudo kill -9 3954  #Eliminamos el proceso que lo utiliza
```