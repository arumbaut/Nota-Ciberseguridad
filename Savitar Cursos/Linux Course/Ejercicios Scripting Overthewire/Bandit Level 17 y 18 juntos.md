Pass next level : x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

```
diff passwords.new passwords.old 
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> BMIOFKM7CRSLI97voLp3TD80NAq5exxk
```

Nos ocurre que al intentar conectar al siguiente nivel nos expulsa de la consola interactiva por lo que necesitamos intentar inyectar comandos mediante el ssh antes de que nos expulse
Ej en la conexion ssh
```
sshpass -p 'x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO' ssh bandit18@bandit.labs.overthewire.org -p 2220 whoami

Solicitamos una bash
sshpass -p 'x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO' ssh bandit18@bandit.labs.overthewire.org -p 2220 bash

Obtenemos la conexion

whoami
bandit18
ls
readme
cat readme
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8   #Pass de bandit19
```

