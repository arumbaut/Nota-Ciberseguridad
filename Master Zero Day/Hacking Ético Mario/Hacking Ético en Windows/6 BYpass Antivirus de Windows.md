- Tags : #window #window_bypass #reverse_shell 

Consiste en evadir el antivirus de la maquina objetivo

Buscaremos en *revshell* [https://www.revshells.com/](https://www.revshells.com/)  los camandos de *powershell* para establecer una *reverseShell* a nuestro equipo

Este codigo de powershell pordemos decirle a la ia que lo ofusque al maximo para que sea muy dificil de leer

Este codigo ofuscado lo ideal es generar un .exe con el e intentar que el objetivo lo ejecute o nosotros ejecutarlo desde la maquina objetivo

Nos creamos un script y le copiamos el codigo este debe ser un script de powershell
ejemplo script.ps1 y le agregamos el codigo ofuscado.

Lo convertimos en .exe con *ps2exe* este se ejecuta en windows 
**Recurso**: ps2exe [https://github.com/MScholtes/PS2EXE](https://github.com/MScholtes/PS2EXE)


```shell
Para correr el programa ps2exe

powershell ise
cd .\PS2EXE-master\Module

#Aqui tambien guardamos el script con la reverseshell

Import-Module .\ps2exe.psm1

Creamos el exe
ps2exe -inputFile ".\script.ps" -output ".\script.exe"
```

Conexión a servidor Publico esperando una conexión.
Servidor publico [vps servidor privado virtual] ideal para recibir conexiones
Mario recomenda Raiola Networks

Al script de powershell lo ponemos a apuntar al ip publico de mi servidor publico escuchando conexiones con nc . 