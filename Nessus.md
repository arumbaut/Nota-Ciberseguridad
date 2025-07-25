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

