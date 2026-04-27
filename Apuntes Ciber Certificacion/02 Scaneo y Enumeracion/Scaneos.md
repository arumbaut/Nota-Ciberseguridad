- Tags : #scaneo_puertos 

### Detectar Host Activos 

```bash
hping3 -1 10.0.0.25

nmap -sn -PE 10.0.0.25

nmap -sn 10.10.10.0/24

arp-scan -g ip

sudo arp-scan -I wlan0 --localnet
```

### Descubrimineto de Puertos

```bash
#Scan General 
nmap -sS -p- --open --min-rate 5000 -Pn -n -vvv 192.168.1.96 -oG ./nmap/allPorts

#Scan especifico
nmap -sSCV -p80 -Pn -n -vvv 192.168.1.96 -oN ./nmap/Target

#Scan ejecutando un script de lua
nmap --script http-enum -p80 192.168.1.96 -oN nmap/webScan


nmap ip -Pn -p- -sUVC -O

nmap ip -Pn -p- -sUV --script=discovery
```


[[03 Host Discovery]]
[[04 Port and Service Discovery]]
[[05 OS Discovery (Banner Grabbing OS Fingerprinting)]]
[[06 Scanning Beyond IDS and Firewall]]