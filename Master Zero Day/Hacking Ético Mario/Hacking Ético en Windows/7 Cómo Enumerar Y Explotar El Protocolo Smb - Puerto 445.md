- Tahgs: #smb #enumeration #enumeration_smb #smb_windows #tools #smbclient #fuerza_bruta #hydra #smbmap

Enumerar Recursos compartido 

```bash

#Enumerar sin tener pass
smbclient -L ip -N

```

Ataque de fuerza bruta con hydra a protocolo smb para descifrar contraseñas

```bash
hydra -l user -P /dictionari_pass.txt smd://ip
```

Enumerar recursos teniendo usuario y password
```bash
#Listar recursos compartido,es necesari tener el usuario y el password
smbclient -L ip -U user 
```

Toot smbmap, herramienta para saber los permisos que tiene un usuario sobre los recursos compartidos

```bash
smbmap -H ip -u 'user' -p 'password'
```

Acceder a un recurso con perisos

```bash
#Es necesario user y pass
smbclient -U 'user' //ip/recurso
```