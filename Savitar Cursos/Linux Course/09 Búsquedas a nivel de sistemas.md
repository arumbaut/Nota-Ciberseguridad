Comandos Find y Locate en Linux: [https://www.hostinger.es/tutoriales/como-usar-comando-find-locate-en-linux/](https://www.hostinger.es/tutoriales/como-usar-comando-find-locate-en-linux/)

Buscar por privilegios SUID y propietario root
```
find / -type f -user root -perm -4000 2>/dev/null
```

Buscar archivos y carpetas donde root sea el propietario y tengan capacidad de escritura 
```
find / -user root -writable 2>/dev/null

```

Buscar archivos donde root sea el propietario y tengan capacidad de ejecución
```
find / -user root -executable -type f 2>/dev/null
```

Buscar archivos donde conozcamos solo parte del nombre
```
find / -name dum\* -type f 2>/dev/null

find / -name \*dum\* -type f 2>/dev/null   #Empieza por algo, dum y termina                                               en otra cosa
find / -name dum\*.sh -type f 2>/dev/null  

```

https://www.hostinger.com/es/tutoriales/como-usar-comando-find-locate-en-linux