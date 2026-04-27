
```bash
#Comando para enumerar SNMPv2 con una cadena de comunidad
snmpwalk -v2c -c public <Dirección IP del Objetivo>

#Comando para buscar software instalado
snmpwalk -v2c -c public <Dirección IP del Objetivo> hrSWInstalledName

#Comando para determinar la cantidad de RAM en el host  
snmpwalk -v2c -c public <Dirección IP del Objetivo> hrMemorySize
```

### NMAP   [[03 SNMP Enumeration]]
```bash
nmap -sU -p 161 --script=snmp-processes <Dirección IP del Objetivo>

#Recupera información sobre el tipo de servidor SNMP y detalles del sistema operativo.
nmap -sU -p 161 --script=snmp-sysdescr <Dirección IP del Objetivo> 
```