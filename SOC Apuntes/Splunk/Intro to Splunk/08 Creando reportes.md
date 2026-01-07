Los reportes son una manera simple de salvar y compartir las búsquedas que realizamos en splunk

```
Comando par agregar contexto geografico a una busqueda
index=security source_type=linux_secure host!=mail* "Failed password" src_ip=*
| iplocation src_ip 

Veremos en Selected Field el campo 
Country


index=security source_type=linux_secure host!=mail* "Failed password" src_ip=*
| iplocation src_ip 
| geostats count by Country

Nos da para poder ver el grafico en forma de mapa

```

Vomos a Save As y lo guardamos como reporte