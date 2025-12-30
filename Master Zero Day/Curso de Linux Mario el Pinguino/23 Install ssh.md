```
apt install openssh-server

systemctl start sshd


El el cliene para no utilizar password 
Generar claves

ssh-keygen

Copiar la privae key al servido ssh
ssh-copi-id user@server
```

Copia de seguridad con SSH
```
#!/bin/bash

zip_file="escritorio.zip"

ssh_user="mario"
ssh_server="192.168.0.44"

remote_path="/home/mario/Escritorio/"

zip -r "$zip_file" .

scp "$zip_file" "$ssh_user@$ssh_server:$remote_path"

if [ $? -eq 0 ]; then
    echo "La operación fue un exito"
else
    echo "Cuidado!! Hubo un error"
fi

rm "$zip_file"
```