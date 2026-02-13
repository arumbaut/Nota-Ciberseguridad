- Tags : #capabilities #limpeas #gtfobins #escalada #escalada_privilegios #tools_escalada_privilegios 

**Recurso**: Script lempeas [https://github.com/peass-ng/PEASS-ng/](https://github.com/peass-ng/PEASS-ng/)
Maquina Shop de *vulnnyx.com*

Las Capabilities son permisos que se le dan a procesos para  que tengan permisos específicos de root sin que sea necesario de que se ejecuten como root

```bash
getcap -r 2>/dev/null

#Descagamos el binario linpeas.sh en el apartado de releases

chmod +x linpeas.sh
./linpeas.sh
```

Los binarios que tengan Capabilities especificas los podemos buscar en gtfobins