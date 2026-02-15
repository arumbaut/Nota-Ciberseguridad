- Tags : #netexec #password_spraying #window #window_explotacion #smb_windows 

Pass spraying 
```bash
#Se hace un ataque de uno a uno es decir cada linea de user con cada linea de pass que en este caso al ser el mismo archivo se revisa su un usuario tiene como pass su propio nombre de usuario
netexec smb ip_victima -u lista_usuarios -p lista_usuarios --no-bruteforce --continue-on-success


#Conectar a un recurso 

netexec smb ip_victima -u user -p pass --shares

```