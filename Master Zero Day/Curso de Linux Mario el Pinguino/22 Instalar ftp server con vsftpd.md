```

apt install vsftpd

systemctl star vsftpd 

Fichero de configuracion 
nano /etc/vsftpd.conf    

Despues de aplicar los cambios reiniciar o recargar el servicio 

systemctl restart|reload vsftpd
```

Scripts Ej Enviar archivos de manera automatica al server FTP
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