- Tags: #side_to_side_vpn #vpn_conf


![[Pasted image 20260501143803.png]]


Esto lo crearemos en etapas
La VPN se configurara en 2 fases

Fase 1 :
1-Creación de la política:  *crypto isakmp policy 10*   # Este numero sera la prioridad para cuando exista mas de una política
2-Le indicaremos que tipo de encriptado utilizaremos: *encryption aes 256*
3-Le diremos que tipo de authentication utilizaremos : *authentication pre-share*
4-Le diremos que Diffie-Hellman group utilizar : *group 5*
5-Por ultimo le diremos la llave y cual sera el dispositivo a conectar (nuestro remote peer). En este caso le diremos al RouterA que su Remote Peer sera RouterB:  *crypto isakmp key CISCO address 198.150.0.2* . Esta es la IP de la interface externa del RouterB

Fase 2 :
1-Necesitamos crear una ACL: Me dirá que trafico se permitirá por la VPN: *ip access-list extended  VPN*
2-Lo siguiente es establecer un set de Transformación este lo que hará es especificar los parámetros de encriptación para la fase 2: *crypto ipsec transform-set RARB esp-aes 256 esp-sha-hmac*
3-Lo siguiente sera crear un mapa para indicarle como aplicar todo esto:  *crypto map VPN-MAP 10 ipsec-isakmp*
4-Aplicaremos el Mapa a una interface
5-Indicarle al NAT que no haga traducciones de nada que valla de la red 10.0.0.0/24 a la 192.168.10.0/24. Esto lo hacemos editando la ACL asociada a nuestro NAT.
### Configuraciones


#### RouterA

```cisco
#### Fase 1 ######
Router_A>enable
Router_A#configure terminal
Router_A(config)#crypto isakmp policy 10
Router_A(config-isakmp)#encryption aes 256
Router_A(config-isakmp)#authentication pre-share
Router_A(config-isakmp)#group 5
Router_A(config-isakmp)#exit
Router_A(config)#crypto isakmp key CISCO address 198.150.0.2

#### Fase 2 ######
Router_A(config)#ip access-list extended VPN
Router_A(config-ext-nacl)#permit ip 10.0.0.0 0.0.0.255 192.168.10.0 0.0.0.255
Router_A(config-ext-nacl)#exit

Router_A(config)#crypto ipsec transform-set RARB esp-aes 256 esp-sha-hmac

Router_A(config)#crypto map VPN-MAP 10 ipsec-isakmp
Router_A(config-crypto-map)#set peer 198.150.0.2  #Indicamos el peer RouterB
Router_A(config-crypto-map)#set pfs group5  #pfs perfet forward secrecy

Router_A(config-crypto-map)#set transform-set RARB #indicamos que set utilizar, creado anteriormente

Router_A(config-crypto-map)#match address VPN  #Indicamos que ACL utilizara, creada anteriormente

Router_A(config)#ip access-list extended NAT   #Modificar la nat para que no nate las direcciones que van de la red 10.0.0.0/24 a 192.168.10.0/24

Router_A(config-ext-nacl)#5 deny ip 10.0.0.0 0.0.0.255 192.168.10.0 0.0.0.255
Router_A(config-ext-nacl)#xit

Router_A(config)#interface gigabitEthernet 0/1
Router_A(config-if)#crypto map VPN-MAP     #Aplicamos el mapa a la interface


Mostrar las configuraciones
Router_A#show crypto ipsec SA
Router_A#show crypto ipsec transform-set

```

Ahora haremos lo mismo en el RouterB


```cisco

#### Fase 1 ######
Router_B>enable
Router_B#configure terminal
Router_B(config)#crypto isakmp policy 10
Router_B(config-isakmp)#encryption aes 256
Router_B(config-isakmp)#authentication pre-share
Router_B(config-isakmp)#group 5
Router_B(config-isakmp)#exit
Router_B(config)#crypto isakmp key CISCO address 198.150.0.2

#### Fase 2 ######
Router_B(config)#ip access-list extended VPN
Router_B(config-ext-nacl)#permit ip 10.0.0.0 0.0.0.255 192.168.10.0 0.0.0.255
Router_B(config-ext-nacl)#exit

Router_B(config)#crypto ipsec transform-set RARB esp-aes 256 esp-sha-hmac

Router_B(config)#crypto map VPN-MAP 10 ipsec-isakmp
Router_B(config-crypto-map)#set peer 198.150.0.2  #Indicamos el peer RouterB
Router_B(config-crypto-map)#set pfs group5  #pfs perfet forward secrecy

Router_B(config-crypto-map)#set transform-set RARB #indicamos que set utilizar, creado anteriormente

Router_B(config-crypto-map)#match address VPN  #Indicamos que ACL utilizara, creada anteriormente

Router_B(config)#ip access-list extended NAT   #Modificar la nat para que no nate las direcciones que van de la red 10.0.0.0/24 a 192.168.10.0/24

Router_B(config-ext-nacl)#5 deny ip 10.0.0.0 0.0.0.255 192.168.10.0 0.0.0.255
Router_B(config-ext-nacl)#xit

Router_B(config)#interface gigabitEthernet 0/1
Router_B(config-if)#crypto map VPN-MAP     #Aplicamos el mapa a la interface

```