[https://www.vulnhub.com/entry/imf-1,162/](https://www.vulnhub.com/entry/imf-1,162/)



#### Identificar cual es la IP del Objetivo 

```
arp-scan -I ens33 --localnet --ignoredups
```


#### Escaneo de todos los puertos

```
nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 192.168.1.23 -oG allPorts
```

#### Escaneo de puertos específicos ejecutando scripts básicos de reconocimiento

```
nmap -p80,443,67 -sCV 192.168.1.23 -oN targetPorts

```

#### Script especifico para enumerar HTTP con nmap hace un fuzzer basico
```
nmap --script http-enum -p80 192.168.1.23 -oN webscan
```

#### Revisar las tecnologías que se utilizan cuando esta el puerto 80 open

```
whatweb http://192.168.1.23 -v
```

#### Buscar en google launchpad la version de Apache o de cualquier servicio que este ejecutando en el servidor puede darnos la version de la distribución del SO

![[Pasted image 20260629122042.png|723]]

![[Pasted image 20260629122116.png|903]]