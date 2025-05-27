
**¿Qué es la Enumeración?**
==La enumeración es el proceso de extraer nombres de usuario, nombres de máquinas, recursos de red, carpetas compartidas y servicios de un sistema o red.== En la fase de enumeración, un atacante crea **conexiones activas con el sistema y envía consultas dirigidas para obtener más información sobre el objetivo**.

#### **Técnicas de Enumeración (Techniques for Enumeration)**

**▪ Extraer nombres de usuario usando direcciones de correo electrónico**  
**▪ Extraer información usando contraseñas predeterminadas**  
**▪ Fuerza bruta contra Active Directory**  
**▪ Extraer información mediante Transferencia de Zona DNS**  
**▪ Extraer grupos de usuarios desde Windows**  
**▪ Extraer nombres de usuario mediante SNMP**  
**▪ Extraer recursos de red y topología usando SNMP**
##### **Services and TCP/UDP ports that can be enumerated**
**▪ TCP/UDP 53:** ==DNS== Zone Transfer 
**▪ TCP/UDP 135:** Microsoft RPC Endpoint Mapper : ==RPC== es un protocolo utilizado por un sistema cliente para solicitar un servicio a un servidor.
**▪ UDP 137:** NetBIOS Name Service (==NBNS==)
**▪ TCP 139:** NetBIOS Session Service (==**SMB over NetBIOS**==)
**▪ TCP/UDP 445**: ==SMB== over TCP (Direct Host)
**▪ UDP 161:** Simple Network Management Protocol (==SNMP==)
**▪ TCP/UDP 389**: Lightweight Directory Access Protocol (==LDAP==)
**▪ TCP 2049**: Network File System (==NFS==)
**▪ TCP 25:** Simple Mail Transfer Protocol (==SMTP==)
**▪ TCP/UDP 162**: ==SNMP Trap== 
**▪ TCP 20/21:** File Transfer Protocol (==FTP==)
**▪ TCP 23:** ==Telnet==

