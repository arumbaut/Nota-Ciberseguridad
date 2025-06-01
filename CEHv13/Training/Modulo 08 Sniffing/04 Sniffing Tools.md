#### Sniffing Tools

▪  Wireshark Source: https://www.wireshark.org
##### **▪ Display Filtering by Protocol** 
##### **▪ Monitoring the Specific Ports** 
1. **tcp.port==23 o ip.addr==192.168.1.100 machine**
2. **ip.addr==192.168.1.100 && tcp.port==23**
##### **▪ Filtering by Multiple IP Addresses** 
 1. **ip.addr == 10.0.0.4 or ip.addr == 10.0.0.5**
##### **▪ Filtering by IP Address** 
 1. **ip.addr == 10.0.0.4**
##### **▪ Other Filters** 
1. **ip.dst == 10.0.1.50 && frame.pkt_len > 400**
2. **ip.addr == 10.0.1.12 && icmp && frame.number > 15 && frame.number < 30**
3. **ip.src == 205.153.63.30 or ip.dst == 205.153.63.30**

##### Displays all TCP resets
**▪ tcp.flags.reset == 1** 

##### Sets a filter for the hex values of 0×33 0×27 0×58 at any offset
**▪ udp contains 33:27:58** 

##### Displays all HTTP GET requests
**▪ http.request** 
##### Displays all retransmissions in the trace
**▪ tcp.analysis.retransmission** 
##### Displays all TCP packets that contain the word “traffic” 
**▪ tcp contains traffic** 

##### Masks out arp, icmp, dns, or other protocols and allows you to view the traffic of your interest
**▪ !(arp or icmp or dns)**
##### Sets a filter for any TCP packet with 4000 as a source or destination port
**▪ tcp.port == 4000** 
#### Displays only SMTP (port 25) and ICMP traffic
**▪ tcp.port eq 25 or icmp** 

##### Displays only traffic in the LAN (192.168.x.x), between workstations and servers—no Internet
**▪ ip.src == 192.168.0.0/16 and ip.dst == 192.168.0.0/16**

**Filters by a protocol (e.g., SIP) and filters out unwanted IPs**
**▪ ip.src != xxx.xxx.xxx.xxx && ip.dst != xxx.xxx.xxx.xxx && sip** 


▪ Capsa Portable Network Analyzer Source: https://www.colasoft.com  
▪ OmniPeek Source: https://www.liveaction.com
▪ RITA (Real Intelligence Threat Analytics) (https://github.com)
▪ Observer Analyzer (https://www.viavisolutions.com)
▪ PRTG Network Monitor (https://www.paessler.com)
▪ Network Performance Monitor (https://www.solarwinds.com)
▪ Xplico (https://www.xplico.org)