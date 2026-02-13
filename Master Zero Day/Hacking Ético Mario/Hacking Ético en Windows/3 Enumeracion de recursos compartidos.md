- Tags : #enumeration #enumeration_windows #window  #enumeration_windows_recursos_compartidos #recursos_compartidos #ASREP-Roast #smb #smbclient

Para esto debemos con anterioridad haber capturado un usuario y su pass que esto lo podemos lograr con un ataque  *ASREP-Roast*

Eplotaremos el pruerto 445 que ejecuta el protocolo *smb*
*Tool*: smbclient

```bash
smbclient -L dominio -user user -password pass

#Listamos recursos compartidos
smbclient -L spookysec.local -user admin -password admini12345

#Conectarnos a un recurso compartido
smbclient \\\\dominio\\recurso -user user -password pass

```