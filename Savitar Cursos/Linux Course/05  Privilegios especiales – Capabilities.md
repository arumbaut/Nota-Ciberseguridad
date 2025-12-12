
Las capabilities son como propiedades que se le agregan a los ficheros , capacidades para hacer ciertas tareas privilegiadas. No por esto quiere decir que sea vulnerable pero hay ciertos ficheros que si tienen ciertos permisos pues si son vulnerables.
Para asignar una capabilities se utiliza el comando 
Ej , existen varias capabilities, buscar mas info 
```
setcap cap_setuid+ep /path/file
```

Ver las capabilities 
```
getcap /path/file

para ver todas
getcap -r / 2>/dev/null 

```

Quitar una capabilities
```
setcap -r /path/file
```

https://manpages.ubuntu.com/manpages/bionic/es/man7/capabilities.7.html

