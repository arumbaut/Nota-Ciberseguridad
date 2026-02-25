- Tags : #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_privilegios_docker #docker 

En la clase actual, exploraremos diversas técnicas para abusar de **Docker** con el objetivo de elevar nuestros privilegios de usuario y escapar del contenedor hacia la máquina host. Examinaremos situaciones específicas y discutiremos las implicaciones de seguridad en cada caso.

Las técnicas que se tratarán en esta clase incluyen:

- Uso de monturas en el despliegue de contenedores para acceder a archivos privilegiados del sistema host. Analizaremos cómo un atacante puede aprovechar las monturas para manipular los archivos del host y comprometer la seguridad del sistema.
- Despliegue de contenedores con la compartición de procesos (**–pid=host**) y permisos privilegiados (**–privileged**). Veremos cómo inyectar un shellcode malicioso en un proceso en ejecución como root, lo que podría permitir al atacante tomar control del sistema.
- Uso de **Portainer** para administrar el despliegue de un contenedor. Discutiremos cómo, mediante el empleo de monturas, un atacante podría ingresar y manipular archivos privilegiados del sistema host y escapar del contenedor.
- Abuso de la **API** de **Docker** por el puerto **2375** para la creación de imágenes, despliegue de contenedores e inyección de comandos privilegiados en la máquina host. Examinaremos cómo un atacante puede explotar la API de Docker para comprometer la seguridad del host y lograr la ejecución de comandos con privilegios elevados.

Al finalizar esta clase, comprenderás las vulnerabilidades potenciales asociadas con Docker y aprenderás a identificar los posibles riesgos de seguridad en entornos basados en contenedores.


*Vías potenciales para escapar de un contenedor de docker para comprometer el host anfitrión*

Para verificar si podemos listar las imágenes de docker del sistema anfitrión buscaremos en el contenedor si tenemos la carpeta */var/run/docker.sock*

La **API de Docker corre por el puerto 2375**  por defecto no esta activa pero se puede habilitar para hacerle peticiones desde el exterior del host .
Desde dentro del contenedor para ver si esta activo podemos hacer :
```bash
echo '' > /dev/tcp/ip_host_anfitrion/2375

echo '' > /dev/tcp/192.168.1.33/2375
echo $?   #Mostrar el codigo de estado
```

Nos basamos en  [https://book.hacktricks.wiki/en/network-services-pentesting/2375-pentesting-docker.html](https://book.hacktricks.wiki/en/network-services-pentesting/2375-pentesting-docker.html)  para intentar explotar la *API*