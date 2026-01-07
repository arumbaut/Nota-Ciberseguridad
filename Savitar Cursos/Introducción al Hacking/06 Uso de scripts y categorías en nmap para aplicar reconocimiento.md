Los scripts de nmap se escriben en lua y se pueden encontrar en el systema con 
```
lacate .nse

Ver las categorias
lacate .nse | xargs grep "categories" |
lacate .nse | xargs grep "categories" | grp -oP '".*?"' | sort -u | wc -l

-sC Ejecuta una sere de scripts al objetivo, los mas comunes 
nmap -p22 ip -sV -sC

Lanzar Scripts que pertenecen a categorias especificas recomendado
nmap -p22 ip --script="vuln and safe"
nmap -p22 ip --script="vuln or safe"

Nos da que programa o servicio esta utilizando el puerto
lsof -i:80

Nos muestra en que ruta de sistema se esta montando
pwdx pid

Scrip de fuzzin de nmap
nmap -p80 ip --script http-enum

Revierte de exadecimal a texto claro
xxd -ps -r 
```