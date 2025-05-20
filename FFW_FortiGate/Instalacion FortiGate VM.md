
### Descargamos la virtual VM de la urt:
(https://support.fortinet.com/support/#/downloads/vm)
Importante estar registrado en el sitio para poder hacer etas descarga 
### Importamos la VM en VMware 
Desactivamos todas las targetas de red y en la tarjeta de red 2 creamos una LAN network
 Encendemos la VM y dejamos que se ejecute, esta nos pedirá que ingresemos une user: admin y pass el cual será vacío
 Luego ejecutaremos pondremos nuestro password de preferencia en este caso m4sterAdmin
 Después ejecutaremos ciertos comando para evitar que expire la licencia de pruebas
 #config system ntp
 #set ntpsync disable
 #set type custom
 #end
 Reiniciamos la VM
### Configurar las tarjetas de Red
#config system interface
#edit port1
#set mode dhcp
#set role wan
#set alias WAN
#set allowacces https ssh ping
#show

#next
#edit port2
#set mode static
#set role lan
#set alias LAN
#set ip 10.10.10.1/24
#set allowacces https ssh ping
#show sys interface
#end para salir

# Obtener los ip de las interfaces
#get system interface

## Obtener el estado del sistema
#get system status