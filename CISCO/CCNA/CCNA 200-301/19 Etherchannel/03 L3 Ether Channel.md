- Tags: #etherchannel #etherchannel_l3


El ether Chanel de Capa 2 se configura de la siguiente manera dependiendo de la vonfiguracion del puerto si es trunk o access
![[Pasted image 20260419113045.png|630]]


![[Pasted image 20260419113145.png|767]]


```cisco
Poner un puerto en su configuracion de fabrica
sw(config)#default interface f0/1-2
sw(config)#interfce range f0/1-2
sw(config-if)#no switchport
sw(config-if)#channel-group 1 mode active
sw(config-if)#exit
sw(config)#interface port-channel 1
sw(config-if)#ip address 10.0.0.1 255.255.255.0
```