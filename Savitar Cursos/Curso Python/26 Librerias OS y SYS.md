OS
```
Obtener directorio actual 
dir_acual = os.getcwd()

list_dir= os.listdir(dir_actual)

os.path.exists(paht)

os.getenv('Nombre_Var_Entorno')
```


SYS  sirve entre otras cosas para obtener los argumentos que se le envían a un script
```
import sys

sys.argv[0] #Da el nombre del script

len(sys.argv) #Cantidad de argumentos pasados a un script

Mostrar las rutas de python 
sys.path

Lanzando un codigo de estado que indiquemos 
sys.exit(1)


```