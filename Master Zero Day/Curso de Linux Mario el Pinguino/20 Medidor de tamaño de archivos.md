```
#!/bin/bash

archivos=$(ls)

for i in $archivos;do
   if [ -f "$i" ];then
     espacio=$(du -b "$i" | awk '{print $1}')
     echo "El archivo $i ocupa $espacio bytes"
     if [ espacio -gt 1000000 ];then
       rm "$i"
       echo "Eliminamos el archivo $i porque ocupa + de 1 MB"
     fi  
   fi  
done  
```