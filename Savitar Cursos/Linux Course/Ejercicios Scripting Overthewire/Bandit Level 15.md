Pass next level : kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

Conectar a una maquina por ssl , esto lo hacemos con ncat que cuenta con un parámetro para indicar el tipo de conexión.

```
bandit15@bandit:~$ ncat --ssl 127.0.0.1 30001
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo   #Introducimos la pass obtenida anterior

Correct!            #Nos responde
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```