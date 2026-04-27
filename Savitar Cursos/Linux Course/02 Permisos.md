Referencias

- Permisos y derechos en Linux: [https://blog.desdelinux.net/permisos-y-derechos-en-linux/?msclkid=22f8cb88ba8111ecb5d8a3db91f066ab](https://blog.desdelinux.net/permisos-y-derechos-en-linux/?msclkid=22f8cb88ba8111ecb5d8a3db91f066ab)
- Permisos básicos en Linux: [https://www.profesionalreview.com/2017/01/28/permisos-basicos-linux-ubuntu-chmod/](https://www.profesionalreview.com/2017/01/28/permisos-basicos-linux-ubuntu-chmod/)


Ver el tipo de encriptado que se utiliza para las passwords
```
cat /etc/login.defs | grep "ENCRYPT_METHOD"
```

Importante entender que siempre prevalece el permiso del directorio que le precede al archivo. Que quiere decir esto :

Si tenemos un *Directorio* prueba donde tienen todos los permisos todos, es decir  (ugo) y dentro un usuario X crea un *Fichero* que tendrá sus propios permiso el permiso que prevalece por encima de todo es el del *Directorio* por lo tanto si otros tienen todos los permisos cualquiera podrá manipular el *Fichero* creado por el usuario x al igual que los del grupo o el owner . Tener en cuenta esto al momento de analizar la jerarquia de permisos pues hace a un fichero accesible de estar mal configurado y de no entender como funcionan

Para evitar esto se utiliza el Sticki bit en el directorio
```
chmod +t directorio
```

El **sticky bit** es un permiso especial en sistemas UNIX/Linux que se aplica **a directorios**, y sirve para que **los archivos dentro del directorio solo puedan ser borrados , renombrados o modificados por su dueño**, aunque otros usuarios tengan permiso de escritura en ese directorio. Prevalecen los permisos del fichero.