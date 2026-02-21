- Tags: #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_privilegios_python #python #python_hijacking

Cuando hablamos de ‘**Python Library Hijacking**‘, a lo que nos referimos es a una técnica de ataque que aprovecha la forma en la que Python busca y carga bibliotecas para inyectar código malicioso en un script. El ataque se produce cuando un atacante crea o modifica una biblioteca en una ruta accesible por el script de Python, de tal manera que cuando el script la importa, se carga la versión maliciosa en lugar de la legítima.

La forma en que el ataque se lleva a cabo es la siguiente: el atacante busca una biblioteca utilizada por el script y la reemplaza por su propia versión maliciosa. Esta biblioteca puede ser una biblioteca estándar de Python o una biblioteca externa descargada e instalada por el usuario. El atacante coloca su versión maliciosa de la biblioteca en una ruta accesible antes de que la biblioteca legítima sea encontrada.

En general, Python comienza buscando estas bibliotecas en el directorio actual de trabajo y luego en las rutas definidas en la variable sys.path. Si el atacante tiene acceso de escritura en alguna de las rutas definidas en sys.path, puede colocar allí su propia versión maliciosa de la biblioteca y hacer que el script la cargue en lugar de la legítima.

Además, el atacante también puede crear su propia biblioteca en el directorio actual de trabajo, ya que Python comienza la búsqueda en este directorio por defecto. Si durante la carga de estas librerías desde el script legítimo, el atacante logra secuestrarlas, entonces conseguirá una ejecución alternativa del programa.


![](../../../attachments/Pasted%20image%2020260219123941.png)

Teniendo uun script de python example.py en tmp con lo siguiente
![](../../../attachments/Pasted%20image%2020260219124919.png)

Pues podemos hacer un Python Library Hijacking basándonos en el principio de que python buscara la librería hashlib, y si la podemos crear en el mismo directorio del example.py pues este la leerá de aquí y no de la verdadera.

```bash
#Ver el path de python
python3 -c 'import sys; print(sys.path)'
```

![](../../../attachments/Pasted%20image%2020260219125620.png)

Pues nos creamos en /tmp un script hashlib.py
```bash
cd /tmp
nano hashlip.py

#Escribimos
import os

os.system("bash -p")

#Cerramos y nos ejecutamos como manolito el example.py para ver si escalamos al usuario manolito

sudo -u manolito python3 /tmp/example.py 
```

También tener en cuenta que si la librería se encuentra en uno de os últimos directorios del path de python y tenemos permisos de escritura en uno de los directorios anteriores también podíamos crear en este el hashlib.py y funcionaria de la misma manera ya que al igual que en el path del sistema se va buscando de izquierda a derecha hasta encontrar el ejecutable. Basta solo poder ponerlo en un lugar por delante de la librería original. Ocurre igual si podemos modificar una de estas librerias que llama el script