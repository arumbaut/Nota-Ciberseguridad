```
Analizar  todo el trafico de la interface
tcpdump -i wlan0  

Analizar el trafico icmp
tcpdump -i wlan0 icmp

Guardar la salida en un fichero para analizarlo con wireshark
tcpdump -i wlan0 -w trafico.pcap
 
```