- Tags : #volatility3 #window #analisis_windows

**Recurso**:[https://blog.onfvp.com/post/volatility-cheatsheet/](https://blog.onfvp.com/post/volatility-cheatsheet/)


```bash
#Para detectar el profile 
#Todos los plugins de volatility3 tienen delante la palabra del sistema operativo que estamos analizando
vol3.py -f Memoria_Ram_Windows10x64.raw windows.info

#Procesos
vol3.py -f Memoria_Ram_Windows10x64.raw windows.pstree | tee dump/pstree.txt

vol3.py -f Memoria_Ram_Windows10x64.raw windows.pslist | tee dump/pslist.txt

vol3.py -f Memoria_Ram_Windows10x64.raw windows.psscan | tee dump/psscan.txt

#DLL
vol3.py -f Memoria_Ram_Windows10x64.raw windows.dlllist

vol3.py -f Memoria_Ram_Windows10x64.raw windows.dlllist --pid 8890 


#Direcciones de memoria
vol3.py -f Memoria_Ram_Windows10x64.raw windows.memmap --pid 7987

vol3.py -f Memoria_Ram_Windows10x64.raw windows.handles | tee dump/handles.txt


vol3.py -f Memoria_Ram_Windows10x64.raw windows.cmdlines

vol3.py -f Memoria_Ram_Windows10x64.raw windows.filescan

vol3.py -f Memoria_Ram_Windows10x64.raw windows.dumpfiles --pid=897


#Network
vol3.py -f Memoria_Ram_Windows10x64.raw windows.netscan

vol3.py -f Memoria_Ram_Windows10x64.raw windows.netstat

#Registros
vol3.py -f Memoria_Ram_Windows10x64.raw windows.hashdump

vol3.py -f Memoria_Ram_Windows10x64.raw windows.registry.hivelist

vol3.py -f Memoria_Ram_Windows10x64.raw windows.registry.printkey

vol3.py -f Memoria_Ram_Windows10x64.raw windows.registry.printkey 



```