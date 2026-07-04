- Tags: #vtp 

Este protocolo se encarga de esparcir las VLANs configuradas en un switch centrar hacia el resto de switches en la red evitando así que se tengan que crear la VLANs manualmente en cada uno de estos, ahorrando tiempo y recurso,  se utiliza cuando tenemos un gran numero de dispositivos.

#### Necesario para la configuracion de VTP en los SW


![[Pasted image 20260419121254.png|716]]

### Cada SW tendra un rol especifico.

El sw Server que propagara las VLANs y los clientes que recibirán las VLANs. Hay un tercer modo que es *transparent*  esto lo que hace es que el SW configurado en transparent mode no participa en la comunicación VTP, sin embargo si reenviara los mensajes VTP a los demas dipositivos


![[Pasted image 20260419121545.png|708]]


![[Pasted image 20260419122226.png|716]]

Hay algo muy importante este protocolo a tener en cuenta que es el numero de revision  que es el que va actualizando la información de las VLANs en todos los clientes . Cada vez que se agrega o quita una vlan en el servidor este envía un mensaje vtp que tiene un nuevo numero  de revision para mantener actualizado a todos los clientes vtp . Por que hay que tener cuidado, pues si por error agregamos otro VTP server con un numero de mensaje mayor que el que esta en la red y tiene una configuración distinta a nuestro server original pues crearía un caos en la red y ni pensar si no tiene ninguna VLAN configurada pues nos limpiaría todas las vlan en los clientes.


El VLAN Pruning es una función de **ahorro de ancho de banda**, no de gestión de base de datos.
- **Sin Pruning:** Si el Switch A envía un mensaje de _broadcast_ en la VLAN 10, ese mensaje viaja por todos los Trunks a todos los switches de la red, aunque los otros switches no tengan ningún puerto en la VLAN 10. Es un desperdicio.
    
- **Con Pruning:** Los switches "hablan" entre ellos y se dicen: _"Oye, yo no tengo a nadie en la VLAN 10, así que no me mandes basura de esa VLAN"_. El switch servidor entonces **deja de reenviar ese tráfico** por ese Trunk específico.
- Se activa desde el SW mode server con `SW1(config)#vtp pruning` 

![[Pasted image 20260419131610.png|801]]

![[Pasted image 20260419131908.png|795]]