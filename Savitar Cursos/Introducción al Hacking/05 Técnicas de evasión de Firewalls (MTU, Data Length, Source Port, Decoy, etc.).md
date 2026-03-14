- Tags : #nmap #nmap_evasion

```bash
#Utilizando fragmentacion de paquetes para evadir
nmap -p22 ip -f

#Filtro de wirwshark para paquetes fragmentados
ip.flag.mf==1

#Con el parametro mtu tambien se puede llegar a evadir el firewall pasandole una mtu(son multiplos de 8) inferior a la esperado en el firewall

nmap -p22 ip --mtu 8

Parametro -D para hacer un decoy (enmascarar la ip entre otras)

nmap -p22 ip -D IP_Decoy1 IP_Decoy2 ..

Modificar el puerto de origen de la peticion --source-port 53 

nmap -p22 ip -v -n -Pn --source-port 53

Modificacion de tamano del paquete ya que los firewals pueden identificar herramientas debido a este y pueden identificarlas --data-length 21 le suma 21 al valor inicial del paquete

nmap -p22 ip -v -n -Pn --data-length 21

Falsificar la MAC de el equipo

nmap -p22 ip -v -n -Pn --spoof-mac Dell
nmap -p22 ip -v -n -Pn --spoof-mac 11:22:33:44:55 

Selft Scan Este no completa la coneccion TCP se le conoce como escaneo sigiloso

nmap -p- --open -sS --min-rate 5000 ip -v -n -Pn 


```