Ubuntu 24.04
```

sudo apt update
sudo apt upgrade

nos copiamos el .deb de Splunk interprise que lo descargamos de su stio 

dpkg -i splunk-10.0.0-e8eb0c4654f8-linux-amd64.deb

NOs vamos a 
cd /opt/splunk/bin

sudo ./splunk enable boot-start

Nos poe la licencia y nos pide que pongamos el user y pass del usuario administrador de splunk

Reiniciamos y luego nos conectamos a la maquina al puerto 8000
http://10.10.11.134:8000/  

Ponemos las credenciales que agregamos anteriormente
```

Tuorial 

https://medium.com/@justinmangaoang/installing-splunk-on-ubuntu-24-04-7ade150a1bff

# Building a Threat Hunting/Malware Home Lab
https://medium.com/@justinmangaoang/building-a-threat-hunting-malware-home-lab-73af1050a153