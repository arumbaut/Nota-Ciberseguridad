Pass next level  0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

Explotamos el bit suid [s] que tiene un scrip en el home de usuario que permite ejecutar comandos con privilegios del propietario .

```
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
bandit19@bandit:~$ 

Otra forma es abrir una bash y que atienda al privilegio suid
./bandit20-do bash -p
```