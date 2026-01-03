
```
#!/usr/bin/env python3

import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_address = ('localhost', 1234)
server_socket.bind(server_address)

# Limitar el límite de conexiones
server_socket.listen(1)

while True:
    client_socket, client_address = server_socket.accept()
    data = client_socket.recv(1024)

    print(f"\n[+] Mensaje recibido del cliente: {data.decode()}")
    print(f"[+] Información del cliente que se ha comunicado con nosotros: {client_address}")

    client_socket.sendall(f"Un saludo crack\n".encode())
    client_socket.close()
```

```
#!/usr/bin/env python3

import socket

def start_server():
    host = 'localhost'
    port = 1234
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.bind((host, port))
        print(f"\n[+] Servidor en escucha en {host}:{port}")
        s.listen(1)
        conn, addr = s.accept()
        with conn:
            print(f"\n[+] Se ha conectado un nuevo cliente: {addr}")
            while True:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)

start_server()


Conectar al servidor tcp con nc
nc localhost 1234
```


```
#!/usr/bin/env python3

import socket

def start_udp_server():
    host = 'localhost'
    port = 1234

    # UDP
    with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as s:
        s.bind((host, port))
        print(f"\n[+] Servidor UDP iniciado en {host}:{port}")
        while True:
            data, addr = s.recvfrom(1024)
            print(f"\n[+] Mensaje enviado por el cliente: {data.decode()}")
            print(f"[+] Información del cliente que nos ha enviado el mensaje: {addr}")

start_udp_server()


Conectar al servidor udp con nc
nc localhost 1234 -u
```


Cliente
```
import socket

def start_udp_client():
    host = 'localhost'
    port = 1234
    with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as s:
        s.sendto(b"Hola, se tensa mucho", (host, port))

start_udp_client()
```



Los protocolos **TCP** (Transmission Control Protocol) y **UDP** (User Datagram Protocol) son fundamentales en la comunicación de red, y la librería ‘**socket**‘ en Python proporciona las herramientas necesarias para interactuar con ellos. Aquí tienes una descripción detallada de ambos protocolos y el uso de ‘**socket**‘:

**Protocolo TCP**

- **Orientado a la Conexión**: TCP es un protocolo orientado a la conexión, lo que significa que establece una conexión segura y confiable entre el emisor y el receptor antes de la transmisión de datos.
- **Fiabilidad y Control de Flujo**: Garantiza la entrega de datos sin errores y en el mismo orden en que se enviaron. También gestiona el control de flujo y la corrección de errores.
- **Uso en Aplicaciones**: Es ampliamente utilizado en aplicaciones que requieren una entrega fiable de datos, como navegadores web, correo electrónico, y transferencia de archivos.

**Protocolo UDP**

- **No Orientado a la Conexión**: A diferencia de TCP, UDP es un protocolo no orientado a la conexión. Envía datagramas (paquetes de datos) sin establecer una conexión previa.
- **Rápido y Ligero**: UDP es más rápido y tiene menos sobrecarga que TCP, ya que no verifica la llegada de paquetes ni mantiene el orden de los mismos.
- **Uso en Aplicaciones**: Ideal para aplicaciones donde la velocidad es crucial y se pueden tolerar algunas pérdidas de datos, como juegos en línea, streaming de video y voz sobre IP (VoIP).

**Librería ‘socket’ en Python**

La librería ‘**socket**‘ en Python es una herramienta esencial para la programación de comunicaciones en red. Permite a los desarrolladores crear aplicaciones que pueden enviar y recibir datos a través de la red, ya sea en una red local o a través de Internet. Aquí tienes una visión general de la librería ‘**socket**‘:

- **Creación de sockets**: La librería ‘**socket**‘ proporciona clases y funciones para crear sockets, que son puntos finales de comunicación. Puedes crear sockets tanto para el protocolo TCP (Transmission Control Protocol) como para UDP (User Datagram Protocol).
- **Conexiones TCP**: Puedes utilizar ‘**socket**‘ para establecer conexiones TCP, que son conexiones confiables y orientadas a la conexión. Esto es útil para aplicaciones que requieren transferencia de datos confiable, como la transmisión de archivos o la comunicación cliente-servidor.
- **Comunicación UDP**: La librería ‘**socket**‘ también admite la comunicación mediante UDP, que es un protocolo de envío de mensajes sin conexión. Es adecuado para aplicaciones que necesitan una comunicación rápida y eficiente, como juegos en línea o aplicaciones de transmisión de video en tiempo real.
- **Funciones de envío y recepción**: Puedes utilizar métodos como ‘**send()**‘ y ‘**recv()**‘ para enviar y recibir datos a través de sockets. Esto te permite transferir información entre dispositivos de manera eficiente.
- **Gestión de conexiones**: La librería ‘**socket**‘ incluye métodos como ‘**bind()**‘ para asociar un socket a una dirección y puerto específicos, y ‘**listen()**‘ para poner un socket en modo de escucha, lo que le permite aceptar conexiones entrantes.
- **Conexiones cliente-servidor**: Con ‘**socket**‘, puedes crear aplicaciones cliente-servidor, donde un programa actúa como servidor esperando conexiones entrantes y otro actúa como cliente para conectarse al servidor.

En resumen, la librería ‘**socket**‘ en Python proporciona las herramientas necesarias para desarrollar aplicaciones de red, permitiendo la comunicación entre dispositivos a través de diferentes protocolos y ofreciendo control sobre la transferencia de datos. Es una parte fundamental de la programación de redes en Python y se utiliza en una amplia variedad de aplicaciones, desde servidores web hasta aplicaciones de chat y juegos en línea.