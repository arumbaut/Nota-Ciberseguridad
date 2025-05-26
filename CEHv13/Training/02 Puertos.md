**Los  puertos  pueden  ser  cualquier  número  entre  0  y  65.535**

**Puertos  conocidos**

Los  puertos  0  a  1023  se  consideran  conocidos  y  son  asignados  por  The **Internet Assigned Numbers Authority (IANA)** 

**Puertos  Registrados**

Los  puertos  1024  a  49.151  se  consideran  registrados  y  normalmente  se  asignan a  protocolos  propietarios

**Puertos  dinámicos  o  privados**

Los  puertos  49.152  a  65.535  pueden  ser  utilizados  por  cualquier  aplicación  sin  estar registrada  en  **IANA**

# **Tabla de Protocolos, Puertos y Capas TCP/IP**

|   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|
|**Application Layer Protocol**|**Puerto(s)**|**Transport Layer Protocol**|**Puerto(s)**|**Internet Layer Protocol**|**Puerto(s)**|**Link Layer Protocol**|**Puerto(s)**|
|**DHCP**|67, 68 (UDP)|TCP|Depende del servicio|IP|N/A|FDDI|N/A|
|**DNS**|53 (UDP/TCP)|UDP|Depende del servicio|IPv6|N/A|Token ring|N/A|
|**DNSSEC**|53 (UDP/TCP)|SSL(presentacion)|443 (usualmente)|IPsec|N/A|WEP|N/A|
|**HTTP**|80 (TCP)|TLS(presentacion)|443 (usualmente)|ICMP|N/A|WPA|N/A|
|**S-HTTP**|443 (TCP)|||ARP|N/A|WPA2|N/A|
|**HTTPS**|443,8080 (TCP)|||IGRP|N/A|TKIP|N/A|
|**FTP**|20 (data), 21 (control)|||EIGRP|N/A|EAP|N/A|
|**SFTP**|22 (TCP)|||OSPF|N/A|LEAP|N/A|
|**TFTP**|69 (UDP)|||HSRP|N/A|PEAP|N/A|
|**SMTP**|25, 587, 465 (TCP)|||VRRP|N/A|CDP|N/A|
|**S/MIME**|(via SMTP/IMAP/POP)|||BGP|179 (TCP)|VTP|N/A|
|**PGP**|(via SMTP/IMAP/POP)|||||STP|N/A|
|**Telnet**|23 (TCP)|||||PPP|N/A|
|**SSH**|22 (TCP)|||||||
|**SOAP**|80/443 (HTTP/S)|||||||
|**SNMP**|161 (UDP), 162 (UDP)|||||||
|**NTP**|123 (UDP)|||||||
|**RPC**|Dinámico (usualmente TCP)135|||||||
|**SMB**|445 (TCP), Sobre Bios Net137-139 (TCP)|||||||
|**SIP**|5060 (UDP), 5061 (TCP)|||||||
|**RADIUS**|1812, 1813 (UDP)|||||||
|**TACACS+**|49 (TCP)|||||||
|**RIP**|520 (UDP)|||||||
|**POP3**|110 (TCP)|||||||
|**POP3S**|995 (TCP)|||||||
|**IMAP**|143 (TCP)|||||||
|**IMAPS**|993 (TCP)|||||||
|**LDAP**|389 (TCP/UDP)|||||||
|**LDAPS**|636 (TCP)|||||||
|**MySQL**|3306 (TCP)|||||||
|**PostgreSQL**|5432 (TCP)|||||||
|**MSSQL (SQL Server)**|1433 (TCP)|||||||
|**HTTPS (Proxy/Alt. HTTP)**|8080 (TCP)|||||||
|**Redis**|6379 (TCP)|||||||
|**Elasticsearch**|9200 (TCP)|||||||
|**VNC**|5900+ (TCP)|||||||
|**RDP (Remote Desktop)**|3389 (TCP)|||||||
|**Kerberos**|88 (TCP/UDP)|||||||
|**NetBIOS**|137-139 (UDP/TCP)|||||||
