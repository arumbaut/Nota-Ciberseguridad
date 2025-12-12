Correr un proceso y pasarlo al 2 plano

```
firefox &     #Poniendo & al final indocamos lo ponga en 2 plano

jobs  #Nos muestra los procesos que esten en 2 plano enviado por nosotros

fg   #Traerlo al primer plano 
fg %1    #Trae al primer plano el proceso segun el numero que le precede
Ctrl+z  #Ponemos un proceso en estado de suspencion 

bg       #Pone un proceso en 2 plano


pgrep nombre_proceso  #Nos da el id del proceso

kill numero_id_proceso

ps aux    #Muestra todo los procesos se le puede hacer un grepp para                   #encontra un en especifico

ps aux | grep firefox

```