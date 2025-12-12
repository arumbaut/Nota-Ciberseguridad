Pass next level  dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

```
con vim abrimos el documento y le ponemos  :%s/millionth

grep millionth data.txt


```

Para sustituir un caracter por otro recomendable tr, pero para cambiar palabras mejor sed
Ej 
Con tr al intentar sustituir palabras re rompe peor un carácter funciona perfecto 
```
bandit8@bandit:~$ echo 'Esto es una prueba de la leche' | tr ' ' '-'
Esto-es-una-prueba-de-la-leche


bandit8@bandit:~$ echo 'Esto es una prueba de la leche' | tr 'prueba' 'probando'
Esto bs onn proban db ln lbchb

```

Ej sed   estructura para cambiar 's/old_world/new_world/' para + de una coincidencia  's/old_world/new_world/g'
```

bandit8@bandit:~$ echo 'Esto es una prueba de la leche' | sed 's/prueba/probando/'
Esto es una probando de la leche

Solo cambia la primera coincidencia
bandit8@bandit:~$ echo 'Esto es una prueba de la prueba que prueba la leche' | sed 's/prueba/probando/'
Esto es una probando de la prueba que prueba la leche

bandit8@bandit:~$ echo 'Esto es una prueba de la prueba que prueba la leche' | sed 's/prueba/probando/g'
Esto es una probando de la probando que probando la leche
```