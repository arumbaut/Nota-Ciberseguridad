**Gestión del Ciclo de Vida del Contenedor**

|**Comando**|**Función**|**Ejemplo de Uso**|
|---|---|---|
|**`docker run`**|Crea y ejecuta un contenedor a partir de una imagen. Es el comando más usado.|`docker run -d -p 8080:80 --name web_app nginx`|
|**`docker start`**|Inicia un contenedor que está parado.|`docker start web_app`|
|**`docker stop`**|Detiene un contenedor en ejecución de forma controlada.|`docker stop web_app`|
|**`docker restart`**|Detiene y vuelve a iniciar un contenedor.|`docker restart web_app`|
|**`docker ps`**|Lista los contenedores en ejecución (sin opciones). Usar `-a` para listar _todos_ (detenidos y en ejecución).|`docker ps -a`|
|**`docker logs`**|Muestra la salida de registro (logs) de un contenedor. Usar `-f` para seguir en tiempo real.|`docker logs -f web_app`|
|**`docker exec`**|Ejecuta un comando dentro de un contenedor en ejecución (ideal para depuración o tareas administrativas).|`docker exec -it web_app /bin/bash`|
|**`docker rm`**|Elimina uno o más contenedores (deben estar detenidos).|`docker rm web_app`|

**Gestión de Imágenes**

| **Comando**         | **Función**                                                                         | **Ejemplo de Uso**                               |
| ------------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------ |
| **`docker pull`**   | Descarga una imagen o un repositorio desde un registro (por defecto Docker Hub).    | `docker pull ubuntu:latest`                      |
| **`docker images`** | Lista todas las imágenes almacenadas localmente.                                    | `docker images`                                  |
| **`docker build`**  | Construye una imagen a partir de un `Dockerfile` en el directorio actual.           | `docker build -t mi-app:v1 .`                    |
| **`docker tag`**    | Crea una etiqueta para una imagen, útil para prepararla para subirla a un registro. | `docker tag mi-app:v1 mi-registro.com/mi-app:v1` |
| **`docker push`**   | Sube una imagen etiquetada a un registro remoto.                                    | `docker push mi-registro.com/mi-app:v1`          |
| **`docker rmi`**    | Elimina una o más imágenes (deben estar sin contenedores asociados).                | `docker rmi nginx`                               |

**Volúmenes (Persistencia de Datos)**

|**Comando**|**Función**|**Ejemplo de Uso**|
|---|---|---|
|**`docker volume create`**|Crea un volumen para almacenamiento persistente.|`docker volume create datos_db`|
|**`docker volume ls`**|Lista todos los volúmenes de Docker.|`docker volume ls`|
|**`docker volume inspect`**|Muestra información detallada sobre un volumen.|`docker volume inspect datos_db`|
|**`docker volume rm`**|Elimina un volumen (debe estar sin contenedores usándolo).|`docker volume rm datos_db`|


**Redes**

| **Comando**                  | **Función**                                                                     | **Ejemplo de Uso**                             |
| ---------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------- |
| **`docker network create`**  | Crea una red definida por el usuario (recomendado para entornos de producción). | `docker network create --driver bridge mi-red` |
| **`docker network ls`**      | Lista todas las redes de Docker.                                                | `docker network ls`                            |
| **`docker network connect`** | Conecta un contenedor en ejecución a una red.                                   | `docker network connect mi-red web_app`        |


Hay dos formas de crear volumenes para generar persistencie independientemente de lo que ocurra con el contenedor una es creando un volumen en en docker o mapeando una carpeta de nuestro sistema operativo en el contenedor 
Ej:

Creación de contenedor con volumen interno
```
Creamos el volumen
docker volume create arch_data_volume

Creamos el contenedor asociado al volumen
docker run -itd --name alpine_arch --mount source=arch_data_volume,target=/mnt/data_dir alpine /bin/sh

Para acceder a la consola y revisas el container  docker exec -it alpine_arch_docker /bin/sh
```

Creacion de contenedor con carpeta mapeada
```
Aqui se mapea la carpeta /home/alexandross/Docker con todo su contenido en el container

docker run -itd --name alpine_arch_docker --mount type=bind,source=/home/alexandross/Docker,target=/mnt/Docker alpine /bin/sh

	Para acceder a la consola y revisas el container  docker exec -it alpine_arch_docker /bin/sh
```
