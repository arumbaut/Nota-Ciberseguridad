
#### **NTP Enumeration**

NTP está diseñado para sincronizar los relojes de las computadoras en red. Utiliza el puerto UDP 123 como su medio principal de comunicación.Comandos de enumeración de NTP como **ntpdate, ntptrace, ntpdc y ntpq** se utilizan para consultar un servidor NTP y obtener información valiosa.

**ntpdate**

Este comando recopila una cantidad de muestras de tiempo de varias fuentes de tiempo.

**ntpdate [-46bBdqsuv] [-a key] [-e authdelay] [-k keyfile] [-o version] [-p samples] [-t timeout] [ -U user_name] server [...]**

**ntptrace**

Este comando determina de dónde obtiene el tiempo el servidor NTP y sigue la cadena de servidores NTP hasta su fuente de tiempo primaria.

**ntptrace [-n] [-m maxhosts] [servername/IP_address]**

**▪ ntpdc** Este comando consulta al demonio ntpd sobre su estado actual y solicita cambios en ese estado. Los atacantes utilizan este comando para recuperar el estado y las estadísticas de cada servidor NTP conectado a la red objetivo.

**ntpdc [ -46dilnps ] [ -c command] [hostname/IP_address]**

**▪ ntpq** 
Este comando monitorea las operaciones del demonio NTP ntpd y determina su rendimiento.  
**ntpq [-46dinp] [-c command] [host/IP_address]**

#### **NTP Enumeration Tools**
**PRTG Network Monitor**  
Fuente: [https://www.paessler.com](https://www.paessler.com)

PRTG supervisa todos los sistemas, dispositivos, el tráfico y las aplicaciones de la infraestructura de TI utilizando diversas tecnologías como SNMP, WMI y SSH. Los atacantes usan PRTG Network Monitor para obtener detalles del servidor SNTP, tales como el tiempo de respuesta del servidor, los sensores activos con el servidor y el tiempo de sincronización.

Some NTP enumeration tools: 
▪ Nmap (https://nmap.org) 
▪ Wireshark (https://www.wireshark.org) 
▪ udp-proto-scanner (https://labs.portcullis.co.uk) 
▪ NTP Server Scanner (http://www.bytefusion.com)


#### **Enumeración de NFS**
NFS es un tipo de sistema de archivos que permite a los usuarios acceder, ver, almacenar y actualizar archivos a través de un servidor remoto. Estos datos remotos pueden ser accedidos por el cliente de la misma manera que se accede a los archivos en el sistema local.La enumeración de servicios NFS permite a los atacantes identificar los directorios exportados, la lista de clientes conectados al servidor NFS junto con sus direcciones IP, y los datos compartidos asociados a estas direcciones IP.

**rpcinfo -p \<Target IP Address\>**

**showmount -e \<Target IP Address\>**
#### **NFS Enumeration Tools**

**▪ RPCScan**  
**Fuente:** [https://github.com](https://github.com)

RPCScan se comunica con los servicios RPC y verifica configuraciones incorrectas en recursos compartidos NFS. Como se muestra en la captura de pantalla, un atacante ejecuta el siguiente comando para enumerar una dirección IP objetivo en busca de servicios NFS activos:
**python3 rpc-scan.py \<Target IP Address\> --rpc**

**▪ SuperEnum**
**Fuente:** [https://github.com](https://github.com)

**SuperEnum** incluye un script que realiza la enumeración básica de cualquier puerto abierto. Un atacante utiliza el script `./superenum` y luego ingresa un archivo de texto llamado “Target.txt” que contiene una dirección IP objetivo o una lista de direcciones IP para llevar a cabo la enumeración.