Pass next level: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

En este nivel nos dicen que debemos clonar un repo que se encuentra en 
```
ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo   por el puerto 2220 y buscar dentro de este la clave 

Ejecutamos
git clone ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo

Nos ddescarga la carpete repo revisamos el repo y encontramos un archivo README.md que contiene .

Nada
   
   Aqui  lo que podemos hacer es ver las anteriores modificaciones del repo para ver si existe alguna pista
   
   Al no encontrar nada y al decir que en produccion no se ponen pass pues nos moveremos de ramas
   
git branch -a    #Muestra todas las ramas 
Solo tiene la master

Pues hay algo en git que son las tags 
En Git, una etiqueta o **tag** sirve básicamente como una rama firmada que no permuta, es decir, siempre se mantiene inalterable. Sencillamente es una cadena arbitraria que apunta a un Commit específico. Puede decirse que un

git tag
secret

git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

Y vemos la pass
   
```


