==Se utiliza para establecer una conexión segura entre un cliente y un servidor, garantizando la privacidad e integridad de la información durante la transmisión==. ==Utiliza una clave simétrica para el cifrado masivo, una clave asimétrica para la autenticación y el intercambio de claves, y códigos de autenticación de mensajes para la integridad de los mensajes. Utiliza el algoritmo RSA con fortalezas de 1024 y 2048 bits. Con TLS, se pueden reducir los riesgos de seguridad, como la manipulación, la falsificación y la interceptación de mensajes==. Una ventaja de TLS es su independencia del protocolo de aplicación. Los protocolos de nivel superior pueden funcionar sobre TLS de forma transparente. TLS ==consta de dos capas: el **TLS Record Protocol  y TLS Handshake Protocol**. 

**TLS Record Protocol**  
El Protocolo de Registro TLS es un protocolo en capas. ==Proporciona conexiones seguras con un método de cifrado como DES==. Protege los datos de la aplicación utilizando las claves generadas durante el apretón de manos y verifica su integridad y origen.

**TLS Handshake Protocol**

El Protocolo de Apretón de Manos TLS permite que el cliente y el servidor se autentiquen mutuamente y seleccionen un algoritmo de cifrado y claves criptográficas antes del intercambio de datos por parte del protocolo de aplicación.El Protocolo de Apretón de Manos TLS opera sobre el Protocolo de Registro TLS y es responsable de producir los parámetros criptográficos del estado de la sesión.


![](attachments/image20250523055914.png)