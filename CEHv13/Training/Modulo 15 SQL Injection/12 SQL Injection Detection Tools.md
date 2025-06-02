#### **▪ OWASP ZAP**

Source: https://www.zaproxy.org

OWASP Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications.

**▪ Damn Small SQLi Scanner (DSSS)**

Source: https://github.com

Damn Small SQLi Scanner (DSSS) is a fully functional SQL injection vulnerability scanner (supporting GET and POST parameters). It scans the web application for various SQL injection vulnerabilities.

**▪ Snort Source: https://www.snort.org**

Some of the expressions that can be blocked by Snort are as follows:

o /User-Agent\x3A\x20[^\r\n]*sleep\x28/i o /[?&]selInfoKey1=[^&]*?([\x27\x22\x3b\x23]|\x2f\x2a|\x2d\x2d)/i

o /(^|&)selInfoKey1=[^&]*?([\x27\x22\x3b\x23]|\x2f\x2a|\x2d\x2d|%27 |%22|%3b|%23|%2f%2a|%2d%2d)/im

o /^\s*?MAIL\s+?FROM\x3a[^\r\n]*?\x28\x29\s\x7b/i

o alert tcp any any -> any $HTTP_PORTS ( msg:"SQL use of sleep function in HTTP header - likely SQL injection attempt"; flow:to_server,established; http_header; content:"User-Agent|3A| "; content:"sleep(",fast_pattern,nocase; pcre:"/User-Agent\x3A\x20[^\r\n]*sleep\x28/i"; metadata:policy balanced-ips drop,policy max-detect-ips drop,policy security-ips drop,ruleset community; service:http; reference:url,blog.cloudflare.com/the-sleepy-user-agent/; classtype:web-application-attack; sid:38993; rev:9; )

Some additional SQL injection detection tools are as follows:

  

▪ Ghauri (https://github.com)

▪ Burp Suite (https://www.portswigger.net)

▪ HCL AppScan (https://www. hcl-software.com)

▪ Invicti (https://www.invicti.com)

▪ SQL Invader (https://www.rapid7.com)

▪ Arachni (https://ecsypno.com)

▪ Qualys WAS (https://www.qualys.com)

▪ Fortify WebInspect (https://www.microfocus.com)

▪ BeSECURE (https://beyondsecurity.com)

▪ SolarWinds® Security Event Manager (https://www.solarwinds.com

▪ sqlifinder (https://github.com) ▪ dotDefender (http://www.applicure.com)

▪ Wapiti (https://wapiti-scanner.github.io)

▪ InsightAppSec (https://www.rapid7.com)

▪ Acunetix Web Vulnerability Scanner (https://www.acunetix.com)

▪ Detectify (https://detectify.com)