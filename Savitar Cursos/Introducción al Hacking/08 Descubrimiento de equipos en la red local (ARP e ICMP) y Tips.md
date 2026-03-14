```bash
nmap -sn ip/24

arp-scan -i eth0 --localnet --ignoredups
 
Se utilizan pero Sabitar no las recomienda 
netdiscover -i eth0   #herramienta

Considerar tambien hacer un descubrimiento de una red mas amplia ya que en ocaciones se suele confundir subneting con segmenteacion ejemplo , si nos dan una ip 192.150.111.2/24 revisamos la red 192.150.111.0/24 y ademas haremos un descubrimiento en una red mas amplia 192.150.0.0/16 
```

Herramienta masscan mas rápida que nmap (nmap escanea unos miles de host por min y masscan unos millones) descubre puertos con un solo envió de paquetes nmap envía paquetes separados para cada puerto. Tener en cuenta para todos los escaners a menor velocidad de scan mas certeza en los datos obtenidos
```
Ej
masscan -p80,8000-8100 --rate=1000

Comun uso por Savitar
masscan -p21,22,23,139,445,80,8080,443,445 -Pn 192.168.0.0/16 --rate=1000

```


```
#!/bin/bash

function ctrl_c(){
  echo -e "\n\n[!] Saliendo...\n"
  tput cnorm; exit 1
}

# Ctrl+C
trap ctrl_c SIGINT

tput civis  #ocultar cursor
for i in $(seq 1 254); do
	time bash -c "ping -c 1 192.168.11.$i" &>/dev/null && echo "[+] Host 192.168.11.$i - Activo" &
done

wait
tput cnorm
```

Si no responde al ping podemos intentar consultar puertos comunes
```
#!/bin/bash

function ctrl_c(){
  echo -e "\n\n[!] Saliendo...\n"
  tput cnorm; exit 1
}

# Ctrl+C
trap ctrl_c SIGINT

tput civis  #ocultar cursor
for i in $(seq 1 254); do
	for port in 21 22 23 25 80 8080 139 443 445;do
		time bash -c "echo '' /dev/tcp/192.168.11.$i/$port" 2>/dev/null && echo "[+] Host 192.168.11.$i - Port $port (Open) " &
	done
done

wait
tput cnorm
```