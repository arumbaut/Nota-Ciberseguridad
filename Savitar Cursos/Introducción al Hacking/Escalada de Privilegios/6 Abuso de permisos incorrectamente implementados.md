- Tags : #escalada #escalada_privilegios #escalada_privilegios_linux #escalada_privilegios_linux_permisos #permisos

En sistemas Linux, los archivos y directorios tienen permisos que se utilizan para controlar el acceso a ellos. Los permisos se dividen en tres categorías: propietario, grupo y otros. Cada categoría puede tener permisos de lectura, escritura y ejecución. Los permisos de un archivo pueden ser modificados por el propietario o por el superusuario del sistema.

El abuso de permisos incorrectamente implementados ocurre cuando los permisos de un archivo crítico son configurados incorrectamente, permitiendo a un usuario no autorizado acceder o modificar el archivo. Esto puede permitir a un atacante leer información confidencial, modificar archivos importantes, ejecutar comandos maliciosos o incluso obtener acceso de superusuario al sistema.

De esta forma, un atacante experimentado podría aprovecharse de esta falla para elevar sus privilegios en el mejor de los casos. Una de las herramientas encargadas de aplicar este reconocimiento en el sistema es ‘**lse**‘. Linux Smart Enumeration (LSE) es una herramienta de enumeración de seguridad para sistemas operativos basados en Linux, diseñada para ayudar a los administradores de sistemas y auditores de seguridad a identificar y evaluar vulnerabilidades y debilidades en la configuración del sistema.

*LSE está diseñado para ser fácil de usar y proporciona una salida clara y legible para facilitar la identificación de problemas de seguridad*. La herramienta utiliza comandos de Linux estándar y se ejecuta en la línea de comandos, lo que significa que no se requiere software adicional. Además, enumera una amplia gama de información del sistema, incluyendo usuarios, grupos, servicios, puertos abiertos, tareas programadas, permisos de archivos, variables de entorno y configuraciones del firewall, entre otros.

A continuación, se os proporciona el enlace directo al proyecto de Github correspondiente a esta herramienta:

- **Linux Smart Enumeration**: [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)


Cuando podemos escribir o tenemos permisos en algunos archivos críticos o directorios en el sistema esto puede derivar en una escalada de privilegios por eso es importante saber como funcionan los permisos en linux

Ej si en /etc/passwd tenemos permisos de escritura podemos engañar al sistema  para obtner una sesion de root

![](../../../attachments/Pasted%20image%2020260219134854.png)

teniendo permisos de escritura en este archivo pues podemos introducir una contraseña harcodeada al usuario root para que cuando nos pida pass no lo lea del /etc/shadow sino de este archivo /etc/passwd burlando asi la seguridad
```bash
openssl passwd 
```

![](../../../attachments/Pasted%20image%2020260219135254.png)

```bash
nano /etc/passwd

#Sustituimos el codigo generado de nuestro pass con openssl pues podremos loguearnos en el sistema como root con la password que proporcionamos
```

![[Pasted image 20260219135438.png]]

```bash
#Encontrar archivos escribibles o con permisos de escritura
find / -writable 2>/dev/null
```

Tambien si tenemos permisos en un Directorio y alguna tarea un script dentro de nuestro directorio aunque no tengamos permisos para modificar el scrip una cosa que si podemos hacer es eliminarlo y crearnos otro con el mismo nombre  con las instrucciones que deseemos y al la tarea ejecutarlo como root ejecutaría nuestro script otorgándonos privilegios de root  

![](../../../attachments/Pasted%20image%2020260219140319.png)

![](../../../attachments/Pasted%20image%2020260219140449.png)

No podemos modificar el ficero example.sh
![](../../../attachments/Pasted%20image%2020260219140806.png)

Pues borramos el example.sh original y nos creamos otro example.sh
```bash
touch example.sh
chmod +x example.sh

nano example.sh

#!/bin/bash
chmod u+s /bin/bash    #Le damos permiso SUID a la bash 
```

Cuando se ejecuta la tarea cron de root pues nos le da el permiso SUID a la bash y luego como usuario simplemente hariamos 
```bash

bash -p
```