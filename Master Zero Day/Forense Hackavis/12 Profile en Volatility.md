- Tags : #volatility #window #analisis_windows #crear_prifile


Podemos descargarnos profiles pre compilados  creados por la fundación de volatility
**Link**: [https://github.com/volatilityfoundation/profiles](https://github.com/volatilityfoundation/profiles)


```bash 
uname -a -r 

#Verificamos la version del quernel de linux
```

Buscamos en el link la version que corresponda al sistema que nos da *uname*

Hacerlo de manera manual 
```bash
sudo apt install gcc make git 

colonamos el voaltility2
git clone https://github.com/volatilityfoundation/volatility
cd volatility
cd tools/linux
sudo su
make #Genera un module.dwarf

#Si nos da warning
rm -rf module.dwarf

nano module.c  #agregamos una linea al final del archivo
MODULE_LICENCE("GPL");

make #Genera un module.dwarf sin warnings

root@ubuntu:/home/alex# zip $(lsb_release -i -s)_$(uname -r)_profile.zip ./volatility/tools/linux/module.dwarf /boot/System.map-$(uname -r)

#Nos copiamos el profile.zip generado a nuestra maquina de analisis y lo copiamos en donde tengamos volatility/volatility/pluginsoverlays/linux

#Utilizamos el volatility con el profile que agregamos
#para ver si lo agrego 
vol.py --info | grep Linux

#Lo utilizamos
vol.py -f memoria.lime --plrofile=LinuxUbuntu18.04-generic-profilex64 linux_banner
```