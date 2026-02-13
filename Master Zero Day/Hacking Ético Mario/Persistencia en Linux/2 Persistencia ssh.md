- Tags : #persistencia #persistencia_linux #persistencia_ssh


Aquí explotaremos de una manera en concreto el protocolo ssh para generar la persistencia a nuestra maquina atacante.

```bash
#Le cambiamos el pass a root

#Como root modificaremos el archivo 

nano /etc/ssh/sshd_config

#Agregamos 

PermitRootLogin yes

#Nos conectamos por ssh como root
ssh root@ip

```