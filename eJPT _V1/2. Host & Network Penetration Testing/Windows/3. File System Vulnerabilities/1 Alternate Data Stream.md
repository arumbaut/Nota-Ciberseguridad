 Los data stream permiten ocultar codigo malicioso en un fichero 
 En el CMD (Windows)
 
```
>notepat text.txt
>del text..txt

#Data Stream
>notepad test.txt:secret.txt

```

WinPEAS : Es una utilidad para test de penetracion para realizar enumeracion en un sitema local de Windows

Teniendo esta herramienta en el sistema la renombraremos (payload) y la pondremos en un fichero Temp en C:\Temp aqui es donde usualmente esconderemos todos los payloads

```
Dentro de Temp
Temp>type payload.exe > windowslog.txt:wenpeas.exe
Temp>notepat windowslog.txt #Lo rellenariamos con datos legitimos de logs para hacerlo creible

#Para ejecutar el exe oculto 
Temp>start windowslog.txt:wenpeas.exe #Da error debemos proseguir

#Necesitaremos hacer un link simbolico
Temp>mklink wupdate.exe C:\Temp\windowslog.txt:wenpeas.exe

#Esto hara que cuando se utilice wupdate en la consola ejecute el software wenpeas

>wupdate

```