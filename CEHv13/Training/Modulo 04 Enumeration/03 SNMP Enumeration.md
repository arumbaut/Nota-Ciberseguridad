**Enumeración SNMP (SNMP Enumeration)**

SNMP es un protocolo de capa de aplicación que ==se ejecuta sobre UDP== y se utiliza para mantener y administrar routers, hubs y switches en una red IP. Los agentes SNMP se ejecutan en redes Windows y Unix sobre dispositivos de red.

La enumeración SNMP es el proceso de crear una lista de cuentas de usuario y dispositivos en una computadora objetivo utilizando SNMP.

SNMP contiene las siguientes dos contraseñas para configurar y acceder al agente SNMP desde la estación de gestión:

▪ **Read Community String** (Cadena de comunidad de solo lectura)
- Permite visualizar la configuración del dispositivo o sistema.    
- Estas cadenas son públicas.  

▪ **Read/Write Community String** (Cadena de comunidad de lectura y escritura)
- Permite cambiar o editar la configuración del dispositivo.    
- Estas cadenas son privadas.    

Cuando los administradores dejan las cadenas de comunidad con la configuración predeterminada, los atacantes pueden usar estas cadenas por defecto (contraseñas) para cambiar o ver la configuración del dispositivo o sistema.

Los atacantes enumeran SNMP para extraer información sobre recursos de red como hosts, routers, dispositivos y recursos compartidos, así como información de red como tablas ARP, rutas...

#### Enumerating SNMP using SnmpWalk

**SnmpWalk**
SnmpWalk es una herramienta de línea de comandos que ==permite a los atacantes escanear numerosos nodos SNMP (Protocolo Simple de Administración de Red) instantáneamente e identificar un conjunto de variables disponibles para acceder a la red objetivo.==

snmpwalk -v1 -c public <Dirección IP del Objetivo>

###### **▪ Comando para enumerar SNMPv2 con una cadena de comunidad “public”:**  
**snmpwalk -v2c -c public <Dirección IP del Objetivo>**▪** 
###### **Comando para buscar software instalado:**  
**snmpwalk -v2c -c public <Dirección IP del Objetivo> hrSWInstalledName**▪ 

###### **Comando para determinar la cantidad de RAM en el host:**  
**snmpwalk -v2c -c public <Dirección IP del Objetivo> hrMemorySize**▪ 

###### **Comando para cambiar un OID a un valor diferente:**  
**snmpwalk -v2c -c public <Dirección IP del Objetivo> \<OID\> \<Nuevo Valor\>**

 ###### **▪ Comando para cambiar el OID sysContact:**
**snmpwalk -v2c -c public <Dirección IP del Objetivo> sysContact \<Nuevo Valor\>**

**Enumeración SNMP usando Nmap**  
**nmap -sU -p 161 --script=snmp-processes <Dirección IP del Objetivo>**

**nmap -sU -p 161 --script=snmp-sysdescr <Dirección IP del Objetivo>** → Recupera información sobre el tipo de servidor SNMP y detalles del sistema operativo.

**nmap -sU -p 161 --script=snmp-win32-software <Dirección IP del Objetivo>** → Recupera una lista de todas las aplicaciones que se están ejecutando en la máquina objetivo.

#### **SNMP Enumeration Tools**

 ▪ **snmp-check (snmp_enum Module);   
 Fuente: [https://www.nothink.org](https://www.nothink.org)
**snmp-check** es una herramienta de código abierto distribuida bajo la Licencia Pública General GNU (GPL). Su objetivo es automatizar el proceso de recopilación de información sobre cualquier dispositivo que soporte SNMP (Windows, sistemas tipo Unix, dispositivos de red, impresoras, etc.).

snmp-check permite la enumeración de dispositivos SNMP y presenta la salida en un formato legible y fácil de usar. Puede ser útil para pruebas de penetración o monitoreo de sistemas.
 
 **▪ SoftPerfect Network Scanner;**
 SoftPerfect Network Scanner puede hacer ping a computadoras, escanear puertos, descubrir carpetas compartidas y obtener prácticamente cualquier información sobre dispositivos de red mediante Windows Management Instrumentation (WMI), SNMP, Protocolo de Transferencia de Hipertexto (HTTP), SSH y PowerShell.

#### **Additional SNMP enumeration tools:** 

▪ Network Performance Monitor (https://www.solarwinds.com) 
▪ OpUtils (https://www.manageengine.com) 
▪ PRTG Network Monitor (https://www.paessler.com) 
▪ Engineer’s Toolset (https://www.solarwinds.com)
