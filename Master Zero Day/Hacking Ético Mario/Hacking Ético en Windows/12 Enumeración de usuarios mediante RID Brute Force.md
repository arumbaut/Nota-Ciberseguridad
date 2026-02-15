- Tags : #rid #recursos #recurso_hackmyvm  #fuerza_bruta #netexec #tools #tools_netexec #smb #window #window_explotacion #window_dc #enumeration_smb 

**Recurso**: Maquina DC01 hackmyvm

*netexec* : Sirve para enumerar recursos compartidos ademas de realizar varios ataques
```bash

apt install netexec

#Enumerar sin tener pass ni usuario, podemos utilizar el usaurio comun guest
netexec smb ip_victima -u 'guest' -p '' --share
```

En un entorno de active directory si el recurso compartido IPC$ (Intern Process Communication, se utiliza par que los procesos se puedan comunicar entre si y poder hacer una adminstración remota del sistema, nunca debe tener permisos de lectura) tiene permisos de lectura, significa que se  pueden enumerar usuarios 

![](../../../attachments/Pasted%20image%2020260213135839.png)
```bash
#Teniendo IPC$ con permisos de lectura pues podremos listar los usuarios del sistema
netexec smb ip_victima -u 'guest' -p '' --rid-brute > usuarios_sin_ordenar

#Filtrar usuarios
cat usuarios_sin_ordenar | tr '\' '' | awk '{print $7}'

```