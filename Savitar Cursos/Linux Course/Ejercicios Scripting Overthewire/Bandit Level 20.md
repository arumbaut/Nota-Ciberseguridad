Este ejercicio va de ponernos a escuchar en un puesto en la maquina y con el binario con permisos suid establecer una conexión a ese puerto y desde nuestra conexión recién abierta enviarle la pass de nivel actual para que responda con la pass del próximo

Nos volvemos a conectar a la maquina y abrimos una conexion con nc en un puerto
```
bandit20@bandit:~$ nc -nlvp 4444
```

Con el ejecutable con permisos suid nos conectamos a este puerto que recién abrimos desde otra terminal
```
bandit20@bandit:~$ ./suconnect 4444

```

Por ultimo enviamos desde la conexión establecida la password 
```
bandit20@bandit:~$ nc -nlvp 4444
Listening on 0.0.0.0 4444
Connection received on 127.0.0.1 57804
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO           #Esto es lo enviado 
EeoULMCra2q0dSkYj561DX7s1CpBuOBt           #Esto es lo recibido
bandit20@bandit:~$ 
```