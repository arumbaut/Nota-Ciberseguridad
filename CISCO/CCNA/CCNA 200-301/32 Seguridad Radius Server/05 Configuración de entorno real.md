
### Nuestra Infraestructura

![[Pasted image 20260512101824.png]]

- Maquina de Alpine
- Router
- Ext-Connection: Conexión por NAT al exterior del entorno virtual donde se encuentra un Servidor Windows Server 2022. *Funcionando como Active directory y como Radius (Servidor de Directivas de Red en Windows)*

Alpine 
```shell
#Le agregamos un direccion IP 
sudo ip addr add 10.0.0.10/24 dev eth0
```

R1
```cisco
Router>enable 
Router#configure terminal 
Router(config)#hostname R1
R1(config)#interface ethernet0/1
R1(config-if)#ip address 10.0.0.1 255.255.255.0
R1(config-if)#no shutdown 

R1(config-if)#exit
R1(config)#interface ethernet0/0
R1(config-if)#ip address dhcp
R1(config-if)#no shutdown 

R1(config)#ip domain name contoso.cisco
R1(config)#username admin secret cisco
R1(config)#enable secret cisco

R1(config)#ip ssh version 2
R1(config)#crypto key generate rsa general-keys modulus 2048

R1(config)#aaa new-model
R1(config)#aaa authentication login Radius-Service group radius local
R1(config)#radius server Radius-Server
R1(config-radius-server)#address ipv4 192.168.1.57 auth-port 1812
R1(config-radius-server)#key m4sterCisco
R1(config-radius-server)#exit

R1(config)#line vty 0 4
R1(config-line)#login authentication Radius-Service
```

### Servidor Windows Server 2021

![[Pasted image 20260512103522.png]]

![[Pasted image 20260512103550.png]]

![[Pasted image 20260512103622.png]]

![[Pasted image 20260512103707.png]]

**Con esto instalamos los roles de AD y Radius Server**
Después seria continuar con la configuración del dominio

### Pasamos a la parte del servidor de Radius

![[Pasted image 20260512103857.png]]

![[Pasted image 20260512103939.png]]

*Creamos un grupo en AD para poner los usuarios que se podrán autenticar y le agregamos los usuarios que queremos que se autentiquen*

![[Pasted image 20260512104206.png]]

*Vamos al servidor de Radius y nos creamos una política para crear los clientes y  permitir la autenticación mediante el servidor a estos equipos*

![[Pasted image 20260512104421.png]]

![[Pasted image 20260512104610.png]]

*Ahora creamos la directiva de red para permitir el acceso*

![[Pasted image 20260512104708.png]]

![[Pasted image 20260512104731.png]]


![[Pasted image 20260512104910.png]]

![[Pasted image 20260512105044.png]]

![[Pasted image 20260512105107.png]]


![[Pasted image 20260512105144.png]]

![[Pasted image 20260512105208.png]]

De aquí en adelante podemos dar siguiente siguiente que funciona o podemos configurar los siguientes paramentros

![[Pasted image 20260512105314.png]]

![[Pasted image 20260512105352.png]]

### Agregamos este

![[Pasted image 20260512105443.png]]


![[Pasted image 20260512105602.png]]

![[Pasted image 20260512105634.png]]

### Lo siguiente son Atributos específicos del proveedor

![[Pasted image 20260512105924.png]]

![[Pasted image 20260512110007.png]]

![[Pasted image 20260512110149.png]]

Esto le indica el nivel de privilegio que tendrán estos usuarios autenticados en el Router 15 es el mas alto 0 el mas bajo que es mínimo privilegio, se pueden asignar permiso a los niveles intermedios en el Router

### El Router: Define el "Qué"

En el router tú defines qué significa, por ejemplo, ser "Nivel 7". Por defecto, el Nivel 7 no tiene permisos especiales, así que tú le dices:
Fragmento de código

```
R1(config)# privilege exec level 7 show running-config
R1(config)# privilege exec level 7 ping
```

Aquí el router dice: "Ok, cualquiera que tenga nivel 7 puede ver la config y hacer pings".
### 2. El RADIUS (NPS): Define el "Quién"
El servidor RADIUS no sabe qué comandos existen en el router, pero tiene la lista de tus empleados. Cuando "alex" se conecta, el NPS mira su directiva y dice:

> _"Alex es un técnico de nivel medio, así que le voy a enviar al router el atributo `shell:priv-lvl=7`"_.

### 3. La Conexión: El apretón de manos
Cuando el router recibe ese `7` desde el NPS:

1. Acepta la entrada de Alex.    
2. Busca en su propia configuración interna qué comandos permitiste para el nivel 7.    
3. Le abre la consola a Alex limitada solo a esos comandos.
### ¿Por qué se hace así y no todo en el router?

Imagínate que tienes **100 routers**.
- **Si no usas RADIUS:** Tendrías que crear el usuario "alex" en los 100 routers. Si Alex renuncia, tienes que entrar en los 100 routers a borrarlo. **Un caos.**    
- **Con RADIUS/NPS:** Solo creas a Alex en el Active Directory. Si quieres que ahora sea Administrador (Nivel 15), solo cambias el número en la Directiva del NPS **una vez**, y automáticamente tiene nivel 15 en los 100 routers.

![[Pasted image 20260512111958.png]]

![[Pasted image 20260512112014.png]]

Ponemos la política por delante de las que deniegan sino se aplicaran antes las de denegación y nunca la nuestra que permite la autenticación.

