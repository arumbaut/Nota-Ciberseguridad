- Tags: #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_path_hijacking #escalada_path_hijacking 

**PATH Hijacking** es una técnica utilizada por los atacantes para **secuestrar** **comandos** de un sistema Unix/Linux mediante la manipulación del **PATH**. El PATH es una variable de entorno que define las rutas de búsqueda para los archivos ejecutables en el sistema.

En algunos binarios compilados, algunos de los comandos definidos internamente pueden ser indicados con una ruta relativa en lugar de una ruta absoluta. Esto significa que el binario busca los archivos ejecutables en las rutas especificadas en el PATH, en lugar de utilizar la ruta absoluta del archivo ejecutable.

Si un atacante es capaz de alterar el PATH y crear un nuevo archivo con el mismo nombre de uno de los comandos definidos internamente en el binario, puede lograr que el binario ejecute la versión maliciosa del comando en lugar de la versión legítima.

Por ejemplo, si un binario compilado utiliza el comando “**ls**” sin su ruta absoluta en su código y el atacante crea un archivo malicioso llamado “**ls**” en una de las rutas especificadas en el PATH, el binario ejecutará el archivo malicioso en lugar del comando legítimo “**ls**” cuando sea llamado.

Para prevenir el PATH Hijacking, se recomienda utilizar **rutas absolutas** en lugar de rutas relativas en los comandos definidos internamente en los binarios compilados. Además, es importante asegurarse de que las rutas en el PATH sean controladas y limitadas a las rutas necesarias para el sistema. También se recomienda utilizar la opción de permisos de ejecución para los archivos ejecutables solo para los usuarios y grupos autorizados.


Compilar scripts con gcc 
```bash
nano test.c
```

```cpp
#include <stdio.h>

int main(){
//Hace que el id de usuario que ejecuta el script se tone a 0	
	setuid(0);  
	print("\n[+] Actualmente somos el usuario:\n\n");	
	system("/usr/bin/whoami")
	print("\n[+] Actualmente somos el usuario:\n\n");	
	system("whoami")
	return 0;
}
```

```bash
#Compilar el script en c
gcc test.c -o test

#Ver los strings imprimibles en el binario generado
string test | grep "whoami" #buscamos si ejecuta el comando whoami
```

Que ocurre en estos casos , pues que si un binario ejecuta la ruta relativa y no la absoluta pues podemos secuestrar el PATH para que ejecute nuestros comandos.

```bash
echo $PATH
```

![](../../../attachments/Pasted%20image%2020260219121711.png)

Cuando se ejecuta un comando ejemplo ls , el sistema lo reconoce y puede ejecutarlo por su ruta absoluta y no obligatoriamente por la ruta absoluta pues porque la ruta absoluta de este se encuentra en la variable global $PATH. Lo que hace el sistema es buscar primeramente en las rutas que se encuentran en esta variable $PATH por el orden en que se encuentran, por lo que si logramos agregar a esta una ruta que contenga una ruta que contenga un binario malicioso este se ejecutara primero que el verdadero del sistema.
Ej
```bash
#Manipulacion de la variable de entorno $PATH para que busque prieramente en un directorion de nuestro interes

export PATH=/tmp/:$PATH #Le agregamos al principio el directorio /tmp
```

![](../../../attachments/Pasted%20image%2020260219122655.png)

Nos creamos un binario whoami en /tmp
```bash
cd /tmp
nano whoami
#Dentro de whoami
bash -p
```

Si ejecutamos el binario test que llama al comando whoami con permisos de root , como modificamos el PATH ahora ejecutara el whoami que creamos en /tmp que lo que hace es lanzar una bash con privilegios del usuario que la ejecuta en este caso root permitiéndonos así escalar privilegios de un usuario a otro. Recordar para este caso el binario test tiene permiso SUID por lo que cualquier otro usuario pude ejecutarlo