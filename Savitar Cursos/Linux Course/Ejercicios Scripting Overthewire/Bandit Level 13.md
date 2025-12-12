Copiar por ssh desde el servidor a mi maquina

Para no tener que escribir la password uso sshpass

```
Descargamos la llave que hay en el nivel 13 
sshpass -p 'FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn' scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private /home/alexandross/Adrian

chmod 600 sshkey.private    #Le damos permisos

Nos conectamos al siguiente nivel con la key
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

Pass nex level para obtener el nuevo pass del de mas arriba
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
