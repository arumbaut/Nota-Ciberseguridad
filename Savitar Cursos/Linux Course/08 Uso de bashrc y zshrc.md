Cuando queremos que devolver el output de un comando a nivel de cadena debemos ponerlo entre $(comando)
Ej
```
echo "Tu IP privada es $(hostname -I | awk '{print $1}') "
```

Estos 2 ficheros se utilizan para crear funciones que utilizaremos global mente en nuestra terminal