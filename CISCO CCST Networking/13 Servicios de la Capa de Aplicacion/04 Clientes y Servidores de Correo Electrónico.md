El correo electrónico es una de las aplicaciones cliente/servidor más populares de Internet. Los servidores de correo electrónico ejecutan software servidor que les permite interactuar con clientes y con otros servidores de correo electrónico mediante la red.

Cada servidor de correo recibe y almacena correspondencia para los usuarios que tienen buzones configurados en el servidor de correo. Cada usuario que tenga un buzón deberá utilizar entonces un cliente de correo electrónico para acceder al servidor de correo y leer estos mensajes. Muchos sistemas de mensajería de Internet utilizan un cliente basado en web para acceder al correo electrónico. Algunos ejemplos de este tipo de cliente son Microsoft 365, Yahoo y Gmail.

Los buzones se identifican con el formato: **usuario@empresa.dominio**

Diversos protocolos de aplicaciones que se usan en el procesamiento del correo electrónico incluyen SMTP, POP3 e IMAP4.

![[Pasted image 20260327142659.png|700]]

**Protocolo Simple de Transferencia de Correo (SMTP)**

SMTP es utilizado por un cliente de correo electrónico para enviar mensajes a su servidor de correo electrónico local. El servidor local entonces decide si el mensaje se destina a un buzón local o si se remite a un buzón de otro servidor.

Si el servidor tiene que enviar el mensaje a un servidor diferente, también se utiliza SMTP entre esos dos servidores. Las solicitudes SMTP se envían al puerto 25.

Haga clic en el botón Reproducir de la figura para ver cómo se usa SMTP para enviar correo electrónico.

![[Pasted image 20260327142726.png|610]]

**Protocolo de oficina de correos (POP3)**

Un servidor que admite clientes POP recibe y almacena mensajes dirigidos a sus usuarios. Cuando el cliente se conecta con el servidor de correo electrónico, los mensajes se descargan al cliente. De manera predeterminada , los mensajes no se retienen en el servidor una vez que el cliente accede a ellos. Los clientes se ponen en contacto con los servidores POP3 en el puerto 110.

**Protocolo de acceso a mensajes de Internet (IMAP4)**

Un servidor que admite el cliente IMAP también recibe y almacena los mensajes dirigidos a sus usuarios. Sin embargo, a diferencia de POP, IMAP conserva los mensajes en los buzones del servidor, a menos que el usuario los elimine. La versión más actual de IMAP es IMAP4, que espera las solicitudes del cliente en el puerto 143.

Existen muchos servidores de correo electrónico diferentes para las diversas plataformas de sistema operativo de la red.