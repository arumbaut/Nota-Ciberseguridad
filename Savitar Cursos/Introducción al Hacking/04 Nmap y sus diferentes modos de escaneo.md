```
Para ver las rutas en mi maquina
route -n 
```

```
Escanar puertos abiertos
nmap -p ip

Puertos especificos
nmap -p22,80 ip

Rango de puertos
nmap -p1-65535 ip

Todos los puertos
nmap -p- ip

Escanear los 500 puertos mas comunes
nmap --top-ports 500 ip

Reportar solo puertos abiertos
nmap --top-ports --open 500 ip

Para ver resultado en tiempo de ejecucion 
nmap -p- 500 ip -v

Que no aplique resolucion DNS
nmap -p- 500 ip -v -n

Controlar el temporizado con el parametro -T (0-5)
nmap -p- 500 ip -v -T3

No hacer descubrimiento de host
nmap -p- -T3 -sT 500 ip -v -n -Pn

TCP conect scan -sT
nmap -p- -T3 -sT 500 ip -v -n 

Captura con tcpdump
tcpdump -i eth0 -w Captura.cap -v

UDP Scan -sU
nmap -p- --open -sU 500 ip -v -n 

Enumerar equipos activos en la red local
arp-scan -I eth0 --localnet

Ping Swit similar al arp-scan
nmap -sn ip/24 | grep -oP '\d{1-3}\.\d{1-3}\.\d{1-3}\.\d{1-3}' | sort

Detectar Systema operativo -O super agresivo
nmap -p- -T3 -sT 500 ip -v -n -O 

Detectar la version de los puertos
nmap -p22,80 -sV ip



```