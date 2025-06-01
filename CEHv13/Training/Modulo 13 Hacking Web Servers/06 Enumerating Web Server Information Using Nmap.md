##### ▪ Discover virtual domains with hostmap:
##### $nmap --script hostmap-bfk \<host\>

##### ▪ Detect a vulnerable server that uses the TRACE method: 
##### nmap --script http-trace -p80 localhost

##### ▪ Harvest email accounts with http-google-email:
##### $nmap --script http-google-email \<host\>

##### ▪ Enumerate users with http-userdir-enum:
##### nmap -p80 --script http-userdir-enum localhost

##### ▪ Detect HTTP TRACE: 
##### $nmap -p80 --script http-trace \<host\>

##### ▪ Check if the web server is protected by a web application firewall (WAF) or IPS:
##### $nmap -p80 --script http-waf-detect --script-args=”http-waf-detect.uri=/testphp.vulnweb.com/artists.php,http-waf-detect.detectBodyChanges” www.modsecurity.org

##### ▪ Fingerprint a WAF 
##### nmap --script=http-waf-fingerprint -p80,443 \<host\>

##### ▪ Enumerate common web applications 
##### $nmap --script http-enum -p80 \<host\>

##### ▪ Obtain robots.txt 
##### $nmap -p80 --script http-robots.txt \<host\>

##### The following are some additional Nmap commands used to extract web server information: 
##### ▪ nmap -sV –O –p target IP address
##### ▪ nmap -sV --script http-enum target IP address
##### ▪ nmap target IP address -p 80 --script = http-frontpage-login
##### ▪ nmap --script http-passwd --script-args http-passwd.root =/ target IP address
