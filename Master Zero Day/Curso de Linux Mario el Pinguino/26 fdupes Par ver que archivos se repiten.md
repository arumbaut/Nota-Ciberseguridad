```
Para saber si un comando esta instalado
command -v cat 
```


Funcion test para evaluar argumentos en los scripts, test es una funcion de evaluacion  
```
#!/bin/bash

# IP y usuario para iniciar sesión al servidor FTP
servidor='192.168.0.25'
usuario='mario-server'

# Ruta del archivo en mi máquina local que quiera subir al servidor FTP
ruta_archivo_local=log.txt

# Ruta y nombre donde queramos guardar el log.txt dentro del servidor
archivo_remoto="/home/mario-server/log.txt"

# Comando para subir el archivo
curl -u $usuario -T "$ruta_archivo_local" ftp://$servidor/$archivo_remoto
```

```
❯ test "$(grep "arg" results.sh)"
❯ lolo=$?                                               
❯ echo $lolo
0   
```