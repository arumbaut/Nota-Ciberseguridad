Info Site
```
https://docs.tenable.com/nessus/Content/DeployNessusDocker.htm#Operators
```

Instalar nesus

```
Descargar de https://www.tenable.com/downloads/nessus
```

Run comand
```
sudo dpkg -i Nessus-10.9.1-debian10_amd64.deb
```

 
 Iniciar 
```
systemctl start nessusd.service
```

Acceder a la interface Web

```
https://NESSUS_HOSTNAME_OR_IP:8834/
```
Detenerlo
```
systemctl stop nessusd.service
```

Prueba en Dcker

Funcional para conectar a nessus y tener u free trial

docker run --name "nessus-managed" -d -p 8834:8834  tenable/nessus:latest-ubuntu


```
docker run --name "nessus-managed" -d -p 8834:8834 -e SC_MANAGED=yes -e USERNAME=******** -e PASSWORD=******* tenable/nessus:latest-ubuntu
```