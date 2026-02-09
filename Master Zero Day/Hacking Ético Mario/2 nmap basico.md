- Tags:

```bash

nmap ip

nmap -sV -sS -sC --min-rate 5000 -n -Pn -vvv ip -oN Desktop/Scan.txt

#Escaneo de Vulnerabilidades
nmap -p 445 --script=vuln ip
```