- Tags : #escalada #escalada_privilegios_python #recursos_dockerlabs 

**Recurso**: Maquina Library  dockerlabs.es

El concepto aquí es identificar scripts de python que se puedan ejecutar como root y que ademas importen librerías , esto no lleva a poder redefinir una de estas librerías para que ejecute código que nosotros deseemos .

![](../../../attachments/Pasted%20image%2020260210173604.png)

nos creamos un shutil.py en la misma carpeta donde esta el script.py y le introducimos un payload para obtener una bash con priviegios
```py
import os
os.system("bin/bash")
```

Para mitigar esto es necesario que no se tenga permiso de escritura en la carpeta donde se encuentra el script de python que ejecuta codigo com permisos de otro usuario o el usuario root ni sobre el script