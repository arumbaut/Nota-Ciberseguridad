Herramientas 

```
arp-scan

nmap

```

Script
```
#!/bin/bash

arp-scan -I enp0s3 --localnet | grep -v "Interface" | grep -v "Starting" | grep -v "packets" | grep -v "Ending" | awk '{print $1}' > ips.txt

while read -r linea; do

    echo -e "\e[38;5;11mEscaneando con nmap la dirección $linea\e[0m"
    nmap -p- -sS -sC -sV --min-rate=5000 -n -Pn $linea -oN "escaneo_$linea.txt"

done < ips.txt

rm ips.txt
```