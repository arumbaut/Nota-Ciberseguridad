- Tags: #dhcp_router_conf

```cisco
Router#configures terminal
Router(config)#hostname DHCP_SERVER
DHCP_SERVER(config)#ip dhcp pool DHCP_POOL_10.0.0.0
DHCP_SERVER(dhcp-config)#network 10.0.0.0 255.255.255.0
DHCP_SERVER(dhcp-config)#default-router 10.0.0.1
DHCP_SERVER(dhcp-config)#dns-server 8.8.8.8

Indica cuanto tiempo se mantendra en la tabla DHCP la asignacion esta en dias
DHCP_SERVER(dhcp-config)#lease 1 

Excluir Direcciones IP a Ofrecer
DHCP_SERVER(config)#ip dhcp excluded-address 10.0.0.80

Excluir un rango
DHCP_SERVER(config)#ip dhcp excluded-address 10.0.0.100 10.0.0.120 

Mostrar la tabla DHCP
DHCP_SERVER#show ip dhcp binding
```

![[Pasted image 20260430103537.png]]