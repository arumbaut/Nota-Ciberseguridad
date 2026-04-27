### Stati Routing IPv4
![[Pasted image 20260421155838.png|740]]


![[Pasted image 20260421160523.png|752]]

![[Pasted image 20260421160632.png|757]]

#### RouterA
```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#ipv6 route 2001:DB8:10:C::/64 2001:DB8:10:B::1
 
```

#### RouterB
```cisco
RouterB>enable
RouterB#configure terminal
RouterB(config)#ipv6 route 2001:DB8:10:A::/64 2001:DB8:10:B::2
 
```

### Mostrar la Tabla de Rutas de IPV6

```cisco
RouterB#show ipv6 route
```