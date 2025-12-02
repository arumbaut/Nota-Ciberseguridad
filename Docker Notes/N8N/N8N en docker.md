En los repos de kali esta una version segura de docker

Instalar docker. 

```
sudo apt install docker.io -y 
```

Correr y descargar el contendor de N8n

```
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

Para que el contenedor persista 
```
docker run -it -d --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

 **Para detenerlo:**

```
docker stop n8n
```

Para arrancarlo nuevamente:
```
docker start n8n
```

Para ver los logs:
```
docker logs -f n8ns
```