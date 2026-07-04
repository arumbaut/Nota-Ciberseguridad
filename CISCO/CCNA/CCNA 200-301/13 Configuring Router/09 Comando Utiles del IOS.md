
```cisco
r1#show running-config

r1#show ver

r1#show flash

r1#show ip interface brief

r1#show run

r1#show interface f0/0

#Para desactivar la traduccion de nombres DNS para que al equivocarnos en consola no intente resolver con los dns y ahorrarnos tiempo
r1(config)#no ip domain-lookup


```

Salvando las configuraciones al TFTP

```cisco
#Salvando la startup-config en servidor TFTP

Router#copy startup-config tftp:
Address or name of remote host []? 192.168.1.10
Destination filename [Router-confg]? start-conf-save.txt

#Salvando la running-config en servidor TFTP
Router#copy running-config tftp:
Address or name of remote host []? 192.168.1.10
Destination filename [Router-confg]? run-conf-save.txt


#Salvando la IOS del sistema en servidor TFTP
Router#copy flash: tftp:
Source filename []? c2900-universalk9-mz.SPA.155-3.M4a.bin
Address or name of remote host []? 192.168.1.10
Destination filename [c2900-universalk9-mz.SPA.155-3.M4a.bin]? save.c2900-universalk9-mz.SPA.155-3.M4a.bin
```