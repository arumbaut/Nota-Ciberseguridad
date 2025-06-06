El objetivo del hacking de OT (Tecnología Operacional) es dañar o interrumpir los procesos empresariales a través de los sistemas de control industrial en distintos sitios de fabricación. Debido a la interconectividad entre los sistemas de TI y los de OT, estos últimos se han visto expuestos a numerosas amenazas a través de sensores remotos, controladores con conexión Wi-Fi, dispositivos USB usados para actualizar software/firmware, servicios en la nube (como SCADA como servicio), entre otros.

**OT Hacking Methodology** 

The following are the different phases of hacking an OT network:
▪ Information Gathering: El primer paso en el hacking de una red OT es la recopilación de información sobre la red y los sistemas OT objetivo mediante diversas técnicas de footprinting y reconocimiento.

Identifying ICS/SCADA Systems using Shodan
Source: https://www.shodan.io
Search for Modbus-enabled ICS/SCADA systems:
**port:502** (Retrieves all the ICS/SCADA systems with Modbus port 502 enabled)

**Information-Gathering Tools**
▪ Kamerka-GUI Source: https://github.com
▪ SearchDiggity (https://bishopfox.com)
▪ Zeek (https://zeek.org)
▪ Criminal IP (https://www.criminalip.io)
▪ ZoomEye (https://www.zoomeye.hk)
▪ ONYPHE (https://www.onyphe.io)

**Scanning ICS/SCADA Systems using Nmap**
**▪ Identifying Open Ports and Services**

```
nmap -Pn -sT --scan-delay 1s --max-parallelism 1 -p 80, 102, 443, 502, 530, 593, 789, 1089-1091, 1911, 1962, 2222, 2404, 4000, 4840, 4843, 4911, 9600, 19999, 20000, 20547, 34962-34964, 34980, 44818, 46823, 46824, 55000-55003 \<Target IP\>
```

▪ Identifying HMI Systems  
```
nmap -Pn -sT -p 46824 <Target IP>

```
▪ Scanning Siemens SIMATIC S7 PLCs 
```
nmap -Pn -sT -p 102 –script=s7-info <Target IP>

```
▪ Scanning Ethernet/IP Devices 
```
nmap -Pn -sU -p 44818 --script enip-info <Target IP>
```

▪ Scanning BACnet Devices 
```
nmap -Pn -sU -p 47808 --script bacnet-info <Target IP>

```
▪ Scanning Ethernet/IP Devices 
```
nmap -Pn -sU -p 44818 --script enip-info <Target IP>
```

▪ Scanning Niagara Fox Devices 
```
nmap -Pn -sT -p 1911,4911 --script fox-info <Target IP>
```

▪ Scanning ProConOS Devices 
```
nmap -Pn -sT -p 20547 --script proconos-info <Target IP>
```

▪ Scanning Omron PLC Devices

```
nmap -Pn -sT -p 9600 --script omron-info <Target IP>

```
```
nmap -Pn -sU -p 9600 --script omron-info <Target IP>
```

▪ Scanning PCWorx Devices 
```
nmap -Pn -sT -p 1962 --script pcworx-info <Target IP>
```

**▪ Vulnerability Scanning**

Una vez que los atacantes recopilan información sobre una red OT objetivo y sus sistemas, realizan un escaneo de vulnerabilidades para identificar exploits y vulnerabilidades disponibles en la infraestructura crítica y en los sistemas OT.Los atacantes utilizan herramientas como SCADA Family para Nessus y Skybox Vulnerability Control para detectar vulnerabilidades en dispositivos, protocolos y aplicaciones tanto de OT como de IT, incluyendo **ICS/SCADA, PLCs, RTUs, HMIs, gateways, desktop computers, and other networked systems.** 

**Tools**

**Vulnerability Scanning Using Nessus Source: https://www.tenable.com**

**Vulnerability Scanning using Skybox Vulnerability Control Source: https://www.skyboxsecurity.com**

Skybox realiza un análisis detallado de rutas a través de redes combinadas de OT e IT, y proporciona información sobre las vulnerabilidades asociadas y los vectores de ataque relacionados.

Skybox puede combinar datos de SCADA e ICS con la información obtenida del análisis de vectores de ataque, fuentes de inteligencia de Skybox, SIEMs (Sistemas de Gestión de Eventos e Información de Seguridad), feeds de inteligencia de amenazas, entre otros.

Sniffing and Vulnerability-Scanning Tools Sniffing Tool: SmartRF Packet Sniffer Source: https://www.ti.com
Vulnerability Scanning Tool: Microsoft Defender for IoT Source: https://www.microsoft.com

**▪ Launch Attacks**

Las vulnerabilidades encontradas se explotan posteriormente para lanzar diversos ataques, como: ataques basados en HMI, ataques de canal lateral, explotación de PLCs, ataques de repetición, ataques por inyección de comandos. Los atacantes utilizan herramientas como **Metasploit y modbus-cli** para hackear dispositivos PLC mediante el protocolo Modbus.

**Software Tools:**
▪ GDB Source: https://www.sourceware.org
▪ OpenOCD Source: https://openocd.org
▪ Binwalk Source: https://github.com
▪ Fritzing Source: https://fritzing.org
▪ Radare2 Source: https://github.com
▪ Ghidra Source: https://github.com

**▪ Gain Remote Access** **&&** **▪ Maintain Access**
Una vez que los atacantes obtienen acceso a los sistemas industriales, manipulan y cambian las operaciones y funciones de los controles industriales, lo que causa tanto daños físicos como financieros a la organización.Después de obtener acceso remoto, los atacantes utilizan estos dispositivos como plataforma para lanzar ataques a otros dispositivos conectados a la red.Una vez que el atacante obtiene acceso al dispositivo, utiliza varias técnicas para mantener el acceso y realizar más explotación.

**OT Hacking Tools**
**▪ mbtget Source: https://github.com**
mbtget is a command-line tool based on a Perl script to perform Modbus transactions

▪ CSET (https://github.com)
▪ Attkfinder (https://gitlab.com)
▪ ICSREF (https://github.com)
▪ ICSFuzz (https://github.com)
▪ ISF (https://github.com)

**Listed below are a few international organizations that alert companies of threats and provide IT/OT solutions to protect the OT industries against cyber-attacks.**

▪ OTCC Source: https://www.otcybercoalition.org
▪ OT-ISAC Source: https://www.otisac.org
▪ NERC Source: https://www.nerc.com
▪ Industrial Internet Security Framework (IISF) Source: https://www.iiconsortium.org
▪ ISA/IEC-62443 Source: https://www.isa.org

**OT Security Tools**
**▪ Flowmon Source: https://www.flowmon.com**
Flowmon permite a los fabricantes y empresas de servicios públicos garantizar con confianza la fiabilidad de sus redes industriales para evitar tiempos de inactividad y la interrupción de la continuidad del servicio.

▪ Tenable OT Security (https://www.tenable.com)
▪ Nozomi Networks (https://www.nozominetworks.com)
▪ Forescout (https://www.forescout.com)
▪ FortiGuard (https://www.fortinet.com)
▪ RAM2 (https://www.otorio.com)