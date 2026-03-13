- Tags : #volatility2 #window #analisis_windows

**Referencia de comandos**
*Link*: [https://github.com/volatilityfoundation/volatility/wiki/command-reference](https://github.com/volatilityfoundation/volatility/wiki/command-reference)

Volatility es capaz de detectar diversos profiles que son los que utilizaremos para ejecutar los plugins de volatility 

```bash
#Para obtener la info basica de la imagen que estamos analizando y detectar el profile
vol.py -f Memoria_Ram_Windows10x64.raw imageinfo
```

![](../../../attachments/Pasted%20image%2020260310172659.png)

El perfil detectado nos lo copiamos para utilizarlo en la utilización de los plugins

```bash
#Este nos da aun mas informacion
vol.py -f Memoria_Ram_Windows10x64.raw kdbgscan
```

Ahora utilizaremos plugins y para esto necesitamos el profile
```bash
#Identifica estructura de datos de procesos
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 pslist

#Identifica estructura de datos de procesos en forma gerarquica
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 pstree

#Identifica procesos que has sido terminados y que ya no estan entralzados ademas de procesos ocultos
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 psscan

#Identifica procesos que estan ocultos o ya no estan
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 psxview
```


**DLLS**

```bash
#Identifica estructura de datos de dlls
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 dlllist | tee dlllist.txt

#Me descarga todos los dll de la adquisicion y lo ponemos en una carpeta directory
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 dlldump -D directory

#Bajar un DLL especifico 
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 dlldump -D dlls --pid=444 --base=0xkfhsldfsdksld000
```

```bash
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 handles | tee handles.txt

#Proporciona info de los identificadores de seguridad y privilegio de cada proceso
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 getsids | tee getsids.txt

```

Consolas
```bash
#Muestra info de consolas activas en el momento de la adquisicion
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 cmdscan

#Muestra mas Informacion
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 consoles

#Muestra info de los procesos iniciados de una consola de comando
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 cmdlines


#Muestra variables de procesos
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 envars

#Muestra las regiones de memoria de un proceso indicado
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 memmap -p 3390

#Dumpea las regiones de memoria
vol.py -f Memoria_Ram_Windows10 x xx64.raw --profile=Wind10x64 memdump -p 3390 -D dump

#Dumpea el proceso enero
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 procdump -p 3390 -D dumps


```


```bash
#Muestra historial de navegacion del iexplorer
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 iehistory

#Muestra lisado de drivers de un dispositivo  al momento del borcado
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 drivescan | tee driv.txt

#Muestra los archivos 
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 filescan | tee file.txt

#Dumpea el archivo indicado
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 dumpfiles -Q offset -D dumps/

#Dumpea los archivos con las extensio indicada
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 dumpfiles -D dumps/ -r evx$ -i -S
```

Networking
```bash
#Depreado
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 netscan
```

Componentes del registro
```bash
#Muestra regiones del registros
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 hivelist

#Muestra regiones del registros
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 printkey

#Dumpear 
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 hivedump 

#Dumpear 
vol.py -f Memoria_Ram_Windows10x64.raw --profile=Wind10x64 hivedump -o offset
```














