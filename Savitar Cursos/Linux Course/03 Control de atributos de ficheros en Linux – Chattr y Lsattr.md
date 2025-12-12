Los ficheros importante en linux mayormente tienen una copia de seguridad creada por el propio sistema .  Investigar mas sobre los atributos
https://rm-rf.es/chattr-y-lsattr-visualizar-y-modificar-atributos-en-sistemas-de-ficheros-linux/#:~:text=El%20primer%20comando%2C%20lsattr%20permite,chmod%2C%20chown%2Csetfacl%E2%80%A6)

https://programmerclick.com/article/5604675172/
Ej
```
──(alexandross㉿Alexandross)-[~]
└─$ ls -l /etc/passwd                       
.rw-r--r-- root root 3.3 KB Mon Dec  1 23:12:08 2025  /etc/passwd
                                                                            
Copia                                                                   
┌──(alexandross㉿Alexandross)-[~]
└─$ ls -l /etc/passwd-
.rw-r--r-- root root 3.3 KB Mon Dec  1 23:12:08 2025  /etc/passwd-
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~]
└─$ ls -l /etc/shadow
.rw-r----- root shadow 1.4 KB Mon Dec  1 23:12:08 2025  /etc/shadow
                                                            
Copia                                                                  
┌──(alexandross㉿Alexandross)-[~]
└─$ ls -l /etc/shadow-
.rw-r----- root shadow 1.4 KB Thu Nov  6 07:21:35 2025  /etc/shadow-
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~]
└─$ 


```

lsattr se utiliza para listar los atributos de los archivos y ficheros
```
$ lsattr /etc/passwd
--------------e------- /etc/passwd

```

chattr se utiliza para cambiar los atributos de los archivo y ficheros (permisos avanzados), con ello podemos dar propiedades especiales a los archivos y ficheros
Ej: Si a un fichero o archivo le damos la propiedad +i o inmutable ni siquiera el usuario root podra eliminar este fichero

```
chattr +i file.txt
```

Ej Real
```
──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ sudo chattr +i poliglot.jpg
[sudo] password for alexandross: 
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ ll                      
.rw-rw-r-- alexandross alexandross  94 B  Sat Aug 23 09:55:45 2025  apache2.conf
.rw-rw-r-- alexandross alexandross 230 KB Mon Aug 18 20:45:17 2025  poliglot.jpg
.rw-rw-r-- alexandross alexandross 230 KB Sat Aug 23 11:56:00 2025  polyglot.php
.rw-rw-r-- alexandross alexandross  93 B  Wed Aug 20 20:33:48 2025  'test .php5'
.rw-rw-r-- alexandross alexandross 123 B  Sat Aug 23 11:09:40 2025  test.php
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ lsattr poliglot.jpg     
----i---------e------- poliglot.jpg
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ sudo rm poliglot.jpg           
rm: cannot remove 'poliglot.jpg': Operation not permitted
                                                                                                                                                 
┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ 

```