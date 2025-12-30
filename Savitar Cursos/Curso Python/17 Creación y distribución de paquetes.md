Cada directorio debe de tener un archivo `__init__.py`  paara que python este conciente de la estructura de directorio que creamos


**Creación de Paquetes**

Para crear un paquete, primero se organiza el código en módulos y subpaquetes dentro de una estructura de directorios. Cada paquete en Python debe contener un archivo especial llamado ‘**__init__.py**‘, que puede estar vacío, pero indica que el directorio es un paquete de Python. Este archivo también puede contener código para inicializar el paquete.

**Estructura de Directorios**

La estructura típica de un paquete podría incluir directorios para documentación, pruebas y el propio código, así como archivos de configuración para la instalación y la distribución del paquete.

**Archivos de Configuración**

Los archivos ‘**setup.py**‘ y ‘**pyproject.toml**‘ son fundamentales en la creación de paquetes. Contienen metadatos y configuraciones necesarios para la distribución del paquete, como el nombre del paquete, versión, descripción y dependencias.

**Distribución de Paquetes**

Para distribuir un paquete, se suele utilizar el Python Package Index (**PyPI**), que es un repositorio de software para la comunidad de Python. Subir un paquete a PyPI lo hace accesible para otros desarrolladores mediante herramientas de gestión de paquetes como ‘**pip**‘.

**Instalación Global**

Al distribuir un paquete, los usuarios pueden instalarlo a nivel global en su entorno de Python, lo que significa que estará disponible para todos los proyectos en ese entorno. Esta es una manera eficaz de compartir código y permitir que otros se beneficien y contribuyan al trabajo que has hecho.

