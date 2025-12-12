Pass next level: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

Este nivel se basa en las tareas cron revisamos las tareas cron asociadas al user del siguiente nivel y vemos que ejecuta un archivo .sh que lo que hace es copiar la password de el a un directorio que sus permisos están mal configurados y tenemos permisos de lectura

```
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ 

bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv


#Obtenemos la password
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q     
```

Herramienta pspy permite monitorizar los comandos que se están ejecutando en el sistema a intervalos regulares de tiempo . [DominicBreuker](https://github.com/DominicBreuker)[  
](https://github.com/DominicBreuker/pspy)

```
ps -eo command
```