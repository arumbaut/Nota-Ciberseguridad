Pass next level: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

En este nivel nos dicen que debemos clonar un repo que se encuentra en 
```
ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo   por el puerto 2220 y buscar dentro de este la clave 

Ejecutamos
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo

Nos ddescarga la carpete repo revisamos el repo y encontramos un archivo README.md que contiene .

   1 │ # Bandit Notes
   2 │ Some notes for level29 of bandit.
   3 │ 
   4 │ ## credentials
   5 │ 
   6 │ - username: bandit29
   7 │ - password: xxxxxxxxxx
   
   Aqui  lo que podemos hacer es ver las anteriores modificaciones del repo para ver si existe alguna pista
   
   git log    #Nos encontramos con algo muy interesane
   
   commit b0354c7be30f500854c5fc971c57e9cbe632fef6 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:19 2025 +0000

    fix info leak
    
Miraremos cuales fueron los cambios aplicados en este log

git show b0354c7be30f500854c5fc971c57e9cbe632fef6    
   
commit b0354c7be30f500854c5fc971c57e9cbe632fef6 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:19 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx

Y vemos la pass
   
```