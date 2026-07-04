- Tags : #port_security
#### Port Security 
#port_security 

La idea de por security es que el SW acepte frames de las direcciones MAC conectadas a los puertos de SW y que descarte los frames de los dispositivos que no están conectados al SW

Par aesto se construye una tabla separada a la tabla de MAC 

![[Pasted image 20260411140157.png|748]]

### Mecanismos para detectar un Frame Malicioso 

![[Pasted image 20260411140546.png|631]]


#### Static  -  Asignamos las MAC que serán permitidas en ese puerto
### Dynamic  -  Indicamos el máximo de direcciones MAC permitirá el puerto ,  2, 4 , etc. Lo que hará es que registra las MAC hasta llegar al máximo indicado y luego descartara paquetes que vengan de oras direcciones MAC. Para desaprender las MAC ya registradas debemos apagar el puerto y encenderlo nuevamente 

## Sticky  -  Trabaja similar al Dynamic salvo que las MAC que registra las guarda en el running-config como si fuera con el método Static 


### Que hacer con ese frame Malicioso que encontramos

Tenemos 3 mecanismos
![[Pasted image 20260411141927.png|745]]
![[Pasted image 20260411142017.png|813]]
![[Pasted image 20260411142521.png|849]]

## OPCION POR DEFECTO
![[Pasted image 20260411142619.png|770]]

Para resetear este tipo de violación es necesario manualmente poner el puerto en shutdown y luego en no shutdown

Resumen de Mecanismos de detección de Frames maliciosos y acciones a tomar

![[Pasted image 20260411143141.png|821]]

### STATIC PORT SECURITY

Es necesario que el puerto al que se le va a activar el port security este en modo Trunk o Access. Aunque muy rara vez se le configura esta capacidad a un puerto en modo trunk

```cisco
sw#enable
sw#configure terminal
sw(conf)#interface f0/24
sw(conf-if)#switchport mode acces
sw(conf-if)#switchport acces vlan 10
sw(conf-if)#switchport port-security
sw(conf-if)#do switchport port-security add
sw(conf-if)#switchport port-security mac-address 000c.29d4.47d5


Establecer un maximo
sw(conf-if)#switchport port-security maximun 3 #Maximo 3 direcciones Mac
sw#show port-security int f0/24
```

Cuando queremos hacer modificaciones en el port security debemos apagarlo con `no switchport port-security ` hacer las nuevas configuraciones y volver a activarlo 

### Sticky 

```cisco

sw(conf)#interface f0/24
sw(conf-if)#no switchport port-security
sw(conf-if)#no switchport port-security mac-address 000c.29d4.47d5
sw(conf-if)#switchport port-security maximun 2
sw(conf-if)#no switchport port-security mac-address sticky
sw(conf-if)#switchport port-security


```
Propiedades del Port Security
```cisco
Switch(config-if)#switchport port-security ?

aging Port-security aging commands

mac-address Secure mac address

maximum Max secure addresses

violation Security violation mode
```

Diferentes restricciones del port security
```cisco
Switch(config)#interface f0/24
Switch(config-if)#switchport port-security violation ?
protect Security violation protect mode

restrict Security violation restrict mode

shutdown Security violation shutdown mode
```