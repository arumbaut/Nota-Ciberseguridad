Pass next level: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

En este nivel nos dicen que debemos clonar un repo que se encuentra en 
```
ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo   por el puerto 2220 y buscar dentro de este la clave 

Ejecutamos
git clone git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo

Nos ddescarga la carpete repo revisamos el repo y encontramos un archivo README.md que contiene .

    1 │ # Bandit Notes
   2 │ Some notes for bandit30 of bandit.
   3 │ 
   4 │ ## credentials
   5 │ 
   6 │ - username: bandit30
   7 │ - password: <no passwords in production!>
   
   Aqui  lo que podemos hacer es ver las anteriores modificaciones del repo para ver si existe alguna pista
   
   Al no encontrar nada y al decir que en produccion no se ponen pass pues nos moveremos de ramas
   
git branch -a    #Muestra todas las ramas 

git checkout dev   #Nos movemos a la rama dev
     
cat README.md

1 │ # Bandit Notes
   2 │ Some notes for bandit30 of bandit.
   3 │ 
   4 │ ## credentials
   5 │ 
   6 │ - username: bandit30
   7 │ - password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

Y vemos la pass
   
```