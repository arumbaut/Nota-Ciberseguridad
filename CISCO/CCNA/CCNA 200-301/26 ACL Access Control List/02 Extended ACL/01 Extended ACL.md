- Tags : #extended_acl

#### Para el filtrado:
- Utilizan  la *Source Address como la Destination Address* 
- Utilizan  el *Source Port como la Destination Port*  tanto del paquete *UDP*  como el *TCP*
- Permite filtrar via las cabeceras del paquete *ICMP*   seleccionando trafico basado en el *Type* y el *Code*  del paquete *ICMP*

- ### Regla de Cisco para el examen CCNA
Las *Extended ACL* se deben aplicar en la interface del router mas cercana al dispositivo de origen  


![[Pasted image 20260428053526.png|750]]

### Ejercicio a ejecutar

![[Pasted image 20260428055524.png|773]]

![[Pasted image 20260428055650.png|773]]


Las Extended ACL van desde los rangos *100 - 199* y *2000 - 2699*

Sintaxis:
- access-list extended < 101-199, 2000-2699> [ permit / deny ] [ ip/tcp/udp/icmp/... ] < source ip > < w.c mask> { *eq* source port optional }  < destination ip > < w.c mask> { *eq* destination port optional }

- ip access-list extended < name >
 [ permit/deny ] [ ip/tcp/udp/icmp/... ] < source ip > < w.c mask> { source port optional }  < destination ip > < w.c mask> { destination port optional }