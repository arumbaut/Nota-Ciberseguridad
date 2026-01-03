
```
import os

if os.path.exists("dirccion\archivo.txt")

Crear Dir
os.mkdir("NombreDirectorio")
os.makedirs("NombreDirectorio/MiSubdirectorio")

Renombrar
os.rename("OldName","NewNombre")

Obtener tamaño
os.path.getsize("nombre")

Concatenear para creal la ruta
ruta=os.path.join("directorio","archivo.txt")

archivo=os.path.basename(ruta)
directorio=os.path.dirname(ruta)

directorio,archivo=os.paht.split(ruta)

Listar
os.listdir()

Eliminar
os.remove("nombre")

os.rmdir("Directorio")

import shutil

shutil.rmtree("Directorio")

```



La librería ‘**os**‘ y el módulo ‘**shutil**‘ en Python son herramientas fundamentales para interactuar con el sistema de archivos, especialmente en lo que respecta a la creación y eliminación de archivos y directorios.

**Creación y Eliminación de Archivos y Directorios**

- **Creación de Directorios**: Utilizando ‘**os.mkdir()**‘ u ‘**os.makedirs()**‘, se pueden crear directorios individuales o múltiples directorios (y subdirectorios) respectivamente.
- **Eliminación**: ‘**os.remove()**‘ se usa para eliminar archivos, mientras que ‘**os.rmdir()**‘ y ‘**os.removedirs()**‘ permiten eliminar directorios y directorios con subdirectorios, respectivamente.
- **Gestión de Rutas**: La sublibrería ‘**os.path**‘ es crucial para manipular rutas de archivos y directorios, como unir rutas, obtener nombres de archivos, verificar si un archivo o directorio existe, etc.

**Módulo shutil**

- **Operaciones de Alto Nivel**: Mientras que os se enfoca en operaciones básicas, ‘**shutil**‘ proporciona funciones de nivel superior, más orientadas a tareas complejas y operaciones en lotes.
- **Copiar y Mover Archivos y Directorios**: ‘**shutil**‘ es especialmente útil para copiar y mover archivos y directorios. Funciones como ‘**shutil.copy()**‘, ‘**shutil.copytree()**‘, y ‘**shutil.move()**‘ facilitan estas tareas.
- **Eliminación de Directorios**: Aunque ‘**os**‘ puede eliminar directorios, ‘**shutil.rmtree()**‘ es una herramienta más poderosa para eliminar un directorio completo y todo su contenido.
- **Manejo de Archivos Temporales**: ‘**shutil**‘ también ofrece funcionalidades para trabajar con archivos temporales, lo que es útil para operaciones que requieren almacenamiento temporal de datos.