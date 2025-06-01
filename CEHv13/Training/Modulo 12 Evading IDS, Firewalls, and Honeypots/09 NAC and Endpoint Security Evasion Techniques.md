Some endpoint security bypassing techniques are as follows: 

▪ VLAN Hopping
▪ Using Pre-authenticated Device
▪ Ghostwriting
▪ Using application whitelisting
▪ Dechaining macros
▪ Clearing memory hooks
▪ Process injection
▪ Using LoLBins
▪ CPL (Control Panel) side-loading
▪ Using ChatGPT
▪ Using Metasploit templates
▪ Windows Antimalware Scan Interface (AMSI)
▪ Hosting phishing sites
▪ Passing encoded commands
▪ Fast flux DNS method
▪ Timing-based evasion
▪ Signed binary proxy execution
▪ Shellcode encryption
▪ Reducing entropy
▪ Escaping the (local) AV sandbox
▪ Disabling event tracing for Windows
▪ Evading “mark of the Syscall”
▪ Spoofing the thread call stack

##### **Bypassing NAC using VLAN Hopping**

==Los atacantes utilizan VLAN hopping para obtener acceso a una red a través del Protocolo de Trunking Dinámico (DTP). Para establecer un trunk con el switch, los atacantes envían paquetes DTP configurando el modo del switch en "dynamic auto" o "dynamic desirable". El trunk establecido crea una vía para que los atacantes accedan a todas las VLANs.==

**VLAN Hopping Tools**

**▪ VLANPWN Source: https://github.com**

**Bypassing NAC using Pre-authenticated Device**

Los atacantes colocan su dispositivo (por ejemplo, una Raspberry Pi) entre el dispositivo pre-autenticado y el servidor de autenticación para garantizar que el tráfico fluya a través de su dispositivo.

**Tools to Bypass NAC using a Pre-authenticated Device**
▪ nac_bypass_setup.sh Source: https://github.com
▪ FENRIR (https://github.com)
▪ NACkered (https://github.com)
▪ Silentbridge (https://github.com)
▪ BITM (https://github.com)

**Bypassing Endpoint Security using Ghostwriting**

Ghostwriting is a bypass technique that involves modifying the structure of the malware code without effecting its functionality.

**Attackers use tools such as Ghostwriting.sh to modify the malware structure.**

▪ Ghostwriting.sh Source: https://github.com

**IDS/Firewall Evading Tools**
  
▪ Traffic IQ Professional (https://www.idappcom.com )
▪ Nmap (https://nmap.org)
▪ Metasploit (https://www.metasploit.com)
▪ PingRAT (https://github.com)
▪ KoviD (https://github.com)
▪ Green Tunnel (https://github.com)
▪ Hyperion (https://nullsecurity.net)

##### ==**Packet Fragment Generator Tool**==s

  ▪ Colasoft Packet Builder (https://www.colasoft.com)
▪ NetScanTools Pro (https://www.netscantools.com)
▪ CommView (https://www.tamos.com)
▪ Ostinato (https://ostinato.org)
▪ WAN Killer (https://www.solarwinds.com)
▪ WireEdit (https://omnipacket.com)