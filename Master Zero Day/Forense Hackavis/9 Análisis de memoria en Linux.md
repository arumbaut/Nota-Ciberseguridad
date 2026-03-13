- Tags: #forense #analisis_linux #volatility2 #linux 

### Análisis de volcado de la RAM de un SO Linux con volatiliy2.

#### Referencia de comandos de Volatility
[https://github.com/volatilityfoundation/volatility/wiki/Command-Reference](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference)

```bash

vol.py --info | grep Linux

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_banner
-linux_banner #Extrae cadena del banner del kernel de linux desde la memoria 

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_pslist | tee dumps/pslist.txt
-linux_pslist #Listamos los procesos activos

cat dumps/pslist | grep syslog
cat dumps/pslist | grep cups  #cups es un proceso para la gestion de impresoras
cat dumps/pslist | grep acpid #encendido y apagado del SO y de gestion de bateria

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_pslist | tee dumps/pstree.txt
-linux_pslist #Lista los procesos en formato de arbol 

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_bash | tee dumps/history.txt


#Analizar la RED a través de la memoria, nos dumpeamos estos comandos para ir viendo las conexiones entrantes y salientes puertos abiertos sockets en conexion y si se esta esfiltrnado info
vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_arp | tee dumps/linux_arp.txt  
-linux_arp #Muestra la tabla arp

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_netstat | tee dumps/linux_netstat.txt
-linux_netstat #Muestra todas las conexiones de red de  nuestro SO y la red en general , muy similar a lo que se puede obtener con el comando de netstat en el sistema

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_ifconfig | tee dumps/linux_ifconfig.txt
-linux_ifconfig #Muestra la configuracion de red


vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_mount | tee dumps/linux_mount.txt
-linux_mount #Muestra los puntos de montajes que hay en el SO

#listar Procesos
vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_psxview | tee dumps/linux_psxview.txt

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_psaux | tee dumps/linux_psaux.txt

vol.py volcado.mem --profile=Linuxmetasploitablex64 linux_lsof | tee dumps/linux_lsof.txt
```


```bash 
pstree -p

ps -e
```

```bash
#Muestra los servicios que arrancan con el SO
systemctl list-unit-files --type=service --state=enabled

#Muestra los servicios que arrancan con el SO
systemctl list-units --type=service --state=running

```


