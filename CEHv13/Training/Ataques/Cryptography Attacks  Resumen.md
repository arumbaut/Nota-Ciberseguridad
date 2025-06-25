 Objectives of Cryptography  

  Confidentiality:  Garantía de que la información sea accesible solo para aquellas personas autorizadas a acceder a ella.

  Integrity:  Confiabilidad de los datos o recursos en términos de prevención de cambios inapropiados y no autorizados.

  Authentication:  Garantía de que la comunicación, documento o dato es genuino..

  Nonrepudiation:  Garantía de que el remitente de un mensaje no pueda negar posteriormente haber enviado el mensaje y que el receptor no pueda negar haberlo recibido.

Types of Cryptography

Symmetric Encryption
El cifrado simétrico requiere que tanto el remitente como el receptor del mensaje posean la misma clave de cifrado

Asymmetric Encryption
El concepto de cifrado asimétrico (conocido como criptografía de clave pública) se introdujo para resolver los problemas de gestión de claves. El cifrado asimétrico   implica tanto una clave pública como una clave privada . La clave pública está disponible públicamente, mientras que el remitente mantiene la clave privada en secreto.

 Cifrado Simétrico 
Más rápido y fácil de implementar, ya que se utiliza la misma clave para cifrar y descifrar los datos.  
Requiere menos potencia de procesamiento. 
Puede implementarse en chips integrados específicos

 Cifrado Asimétrico 
Conveniente de usar, ya que no se requiere la distribución de claves para cifrar mensajes.  
Mayor seguridad.  
Proporciona firmas digitales que no pueden ser repudiadas

  Block cipher:  
Algoritmos deterministas que operan sobre un bloque (un grupo de bits) de tamaño fijo con una transformación invariable especificada por una clave simétrica. La mayoría de los cifrados modernos son cifrados por bloques. Se utilizan ampliamente para cifrar grandes cantidades de datos . 
Ejemplos DES, AES, IDEA,

 (Flujo)  Stream cipher:  Cifrados de clave simétrica en los que los dígitos de texto plano se combinan con un flujo de clave (flujo de dígitos cifrados seudoaleatorios). Ejemplos incluyen RC4, SEAL, etc.


Symmetric Encryption Algorithms

Data Encryption Standard (DES)
Utiliza un algoritmo de cifrado de datos (DEA), un cifrado por bloques , opera con una clave de 56 bits sobre bloques de 64 bits

 Estándar de Cifrado de Datos Triple (3DES)
Cifrado por bloques. Ejecuta el algoritmo DES tres veces con tres claves diferentes. Utiliza un “paquete de claves” que consta de tres claves DES. Cada clave es una clave DES estándar de 56 bits.

Estándar de Cifrado Avanzado (AES)
Es una especificación del Instituto Nacional de Estándares y Tecnología (NIST) para el cifrado de datos electrónicos. También se utiliza para cifrar información digital como datos de telecomunicaciones, financieros y gubernamentales. Las agencias del gobierno de los Estados Unidos lo han estado utilizando para proteger material sensible pero no clasificado. Tiene un tamaño de bloque de 128 bits, con tamaños de clave de 128, 192 y 256 bits para AES-128, AES-192 y AES-256, respectivamente. 

 RC4  
Es un cifrado de flujo simétrico con tamaño de clave variable. Se basa en el uso de una permutación aleatoria.

RC5 es un cifrado de bloque simétrico rápido, diseñado por Ronald Rivest. . Los tamaños de bloque pueden ser de 32, 64 o 128 bits. . La rutina de cifrado tiene tres operaciones fundamentales: suma entera, XOR bit a bit y rotación variable.

RC6 es un cifrado de bloque simétrico derivado de RC5. Es un algoritmo parametrizable con tamaño de bloque, tamaño de clave y número de rondas variables.  

 Blowfish 
Cifrado por bloques simétrico diseñado para reemplazar los algoritmos DES o IDEA.  Este algoritmo divide los datos en bloques de longitud de 64 bits y produce una clave que varía entre 32 bits y 448 bits. Se utiliza en software que va desde herramientas de protección de contraseñas hasta sitios web de comercio electrónico para asegurar pagos. 

Twofish
Fue uno de los cinco finalistas del Gobierno de los EE. UU. para reemplazar al DES. Fue diseñado por   Bruce Schneier ,   John Kelsey ,   Doug Whiting ,   David Wagner ,   Chris Hall  y   Niels Ferguson . es un   cifrado por bloques de 128 bits .

Threefish
Es un   cifrado por bloques simétrico y modificable ("tweakable")  de gran tamaño, en el que   los tamaños del bloque y de la clave son iguales : 256, 512 y 1024 bits. utiliza únicamente   tres operaciones :   ARX (suma, rotación y XOR) , lo que simplifica el código.


Asymmetric Encryption Algorithms

 Digital Signature Algorithm (DSA)
Es un Estándar de Procesamiento de Información Federal para firmas digitales. El NIST propuso el DSA para su uso en el Estándar de Firma Digital (DSS). El DSA ayuda en la generación y verificación de firmas digitales para aplicaciones sensibles y no clasificadas. Crea una firma digital de 320 bits con seguridad de 512 a 1024 bits. Es un algoritmo que se utiliza para proporcionar **firmas digitales** en archivos y correos electrónicos, con el fin de ofrecer **no repudio** y **autenticidad**. **No proporciona confidencialidad ni integridad**.

Rivest–Shamir–Adleman (RSA)
 Sistema de criptografía de clave pública para el cifrado y la autenticación en Internet. Utiliza aritmética modular y teorías elementales de números para realizar cálculos utilizando dos números primos grandes. El sistema RSA se utiliza ampliamente en una variedad de productos, plataformas e industrias.

Diffie–Hellman
Es un protocolo criptográfico que permite a dos partes establecer una clave compartida a través de un canal inseguro. no proporciona ninguna autenticación para el intercambio de claves y es vulnerable a muchos ataques criptográficos. Sin embargo, es la base de muchos mecanismos de autenticación

Elliptic Curve Cryptography (ECC) 
La ECC es una criptografía moderna de clave pública desarrollada para evitar el uso de claves criptográficas de gran tamaño.Este sistema criptográfico asimétrico se basa en la teoría de números y en curvas elípticas matemáticas (una estructura algebraica) para generar claves criptográficas   cortas, rápidas y robustas .


 HASH 
Las funciones hash calculan una representación única de tamaño fijo en bits, llamada resumen de mensaje, de cualquier bloque de información arbitrario. Las funciones de resumen de mensaje destilan la información contenida en un archivo (pequeño o grande) en un único número de longitud fija, típicamente entre 128 y 256 bits. Si se cambia cualquier bit de entrada de la función, cada bit de salida tiene un 50% de probabilidad de cambiar.


 MD5  
MD5 es una función hash criptográfica ampliamente utilizada que toma un mensaje de longitud arbitraria como entrada y produce una huella digital o resumen de mensaje de 128 bits (16 bytes) como salida.Puede utilizarse en una amplia variedad de aplicaciones criptográficas y es útil para aplicaciones de firma digital, verificación de integridad de archivos y almacenamiento de contraseñas.  
Sin embargo, MD5 no es resistente a colisiones; por lo tanto, es mejor usar los algoritmos más recientes, como MD6, SHA-2 y SHA-3.

 MD6  
Utiliza una estructura similar a un árbol de Merkle para permitir el cálculo paralelo a gran escala de hashes para entradas muy largas.

 Message Digest Function: Secure Hashing Algorithm (SHA) 
El cifrado SHA es una serie de cinco funciones criptográficas diferentes, y actualmente tiene tres generaciones: SHA-1, SHA-2 y SHA-3.

SHA-1: Es una función hash de 160 bits que se asemeja al antiguo algoritmo MD5 desarrollado por Ron Rivest. Produce un resumen de 160 bits . Fue diseñada por la Agencia de Seguridad Nacional (NSA) para formar parte del Algoritmo de Firma Digital (DSA). Se utiliza comúnmente en protocolos de seguridad como PGP, TLS, SSH y SSL. 

SHA-2: SHA-2 es una familia de dos funciones hash similares con diferentes tamaños de bloque, utiliza palabras de 32 bits, y SHA-512, que utiliza palabras de 64 bits. 

  SHA-3:  Utiliza una construcción de esponja en la que los bloques de mensaje se combinan con una operación XOR en los bits iniciales del estado. Soporta los mismos tamaños de hash que SHA-2, pero difiere considerablemente en su estructura interna del resto de la familia SHA.

 RIPEMD-160
RACE Integrity Primitives Evaluation Message Digest (RIPEMD) es un algoritmo hash de 160 bits desarrollado por Hans Dobbertin, Antoon Bosselaers y Bart Preneel. Existen versiones de 128, 256 y 320 bits de este algoritmo, denominadas RIPEMD-128, RIPEMD-256 y RIPEMD-320, respectivamente. 

 Hardware-Based Encryption 

Types of hardware encryption devices

  TPM 

El Módulo de Plataforma Confiable (TPM, por sus siglas en inglés) es un criptoprocesador o chip que está presente en la placa base. Puede almacenar de forma segura las claves de cifrado y realizar muchas operaciones criptográficas. El TPM ofrece varias funciones, como autenticar la integridad de la plataforma, proporcionar capacidades de cifrado de disco completo, realizar almacenamiento de contraseñas y brindar protección de licencias de software.

  HSM 
Un módulo de seguridad de hardware (HSM, por sus siglas en inglés) es un dispositivo de seguridad externo adicional que se utiliza en un sistema para el cripto-procesamiento, y puede utilizarse para gestionar, generar y almacenar de forma segura claves criptográficas. 

  USB Encryption 
El cifrado USB es una función adicional para los dispositivos de almacenamiento USB, que ofrece servicios de cifrado integrados. Los dispositivos USB cifrados necesitan un sistema de credenciales en el dispositivo o credenciales basadas en software o hardware desde una computadora. 

  Hard Drive Encryption 
La cifrado de disco duro es una tecnología mediante la cual los datos almacenados en el hardware pueden ser cifrados utilizando una amplia variedad de opciones de cifrado. Los dispositivos de cifrado de disco duro no pueden usar un teclado integrado ni un lector de huellas dactilares; en su lugar, requieren un TPM (módulo de plataforma confiable) o un HSM (módulo de seguridad de hardware). 

 HMAC 
Hash-based message authentication code (HMAC) es un tipo de código de autenticación de mensajes (MAC) que utiliza una clave criptográfica junto con una función hash criptográfica. Se utiliza ampliamente para verificar la integridad de los datos y la autenticación de un mensaje. Este algoritmo incluye una función hash integrada, como SHA-1 o MD5. La solidez del HMAC depende de la función hash integrada, el tamaño de la clave y el tamaño del hash de salida.

Quantum Cryptography
Esta criptografía se procesa con base en la mecánica cuántica, como la distribución de claves cuánticas (QKD), utilizando fotones en lugar de matemáticas como parte del cifrado. En la criptografía cuántica, los elementos de datos se cifran mediante una secuencia de fotones que tienen una característica de giro al viajar de un extremo a otro

Public Key Infrastructure (PKI)
PKI (Infraestructura de Clave Pública) es una arquitectura de seguridad desarrollada para aumentar la confidencialidad de la información intercambiada a través de Internet, que es un entorno inseguro. Incluye hardware, software, personas, políticas y procedimientos necesarios para crear, gestionar, distribuir, usar, almacenar y revocar certificados digitales.
 
 Componentes de la PKI: 
  
  Certificate Management System: 
  Genera, distribuye, almacena y verifica los certificados.
  
  Digital Certificates: 
  Establecen las credenciales de una persona al realizar transacciones en línea.

  Validation Authority (VA): 
  Almacena certificados (junto con sus claves públicas).
  
  Certification Authority (CA): 
  Emite y verifica los certificados digitales.

  End User: 
Solicita, gestiona y utiliza certificados.

  Registration Authority (RA): 
Actúa como verificador para la CA
 
 Digital Signature 
 Una firma digital utiliza criptografía asimétrica  para simular las propiedades de seguridad de una firma en forma digital en lugar de escrita. Es un medio criptográfico de autenticación. La criptografía de clave pública utiliza cifrado asimétrico y ayuda al usuario a crear una firma digital.

Secure Sockets Layer (SSL)
es un protocolo de capa de aplicación desarrollado por Netscape para gestionar la seguridad de la transmisión de mensajes en Internet. requiere un protocolo de transporte fiable, como TCP. Utiliza el cifrado asimétrico RSA (de clave pública) para cifrar los datos transferidos a través de conexiones SSL. Cualquier protocolo de capa de aplicación superior a SSL, como HTTP, FTP y Telnet, puede formar una capa transparente sobre SSL. actúa como árbitro entre el algoritmo de cifrado y la clave de sesión; también verifica el servidor de destino antes de la transmisión y recepción de datos

SSL también ofrece "seguridad de canal"  con tres propiedades básicas: 

▪ Canal privado: todos los mensajes se cifran tras un simple protocolo de enlace para definir una clave secreta.
▪ Canal autenticado: el extremo del servidor de la conversación siempre está cifrado, mientras que el extremo del cliente se autentica opcionalmente.
▪ Canal confiable: la transferencia de mensajes tiene una verificación de integridad

Transport Layer Security (TLS)
Se utiliza para establecer una conexión segura entre un cliente y un servidor, garantizando la privacidad e integridad de la información durante la transmisión. Utiliza una clave simétrica para el cifrado masivo, una clave asimétrica para la autenticación y el intercambio de claves, y códigos de autenticación de mensajes para la integridad de los mensajes. Utiliza el algoritmo RSA con fortalezas de 1024 y 2048 bits. Con TLS, se pueden reducir los riesgos de seguridad, como la manipulación, la falsificación y la interceptación de mensajes. consta de dos capas: el **TLS Record Protocol  y TLS Handshake Protocol**. 

**TLS Record Protocol** Proporciona conexiones seguras con un método de cifrado como DES

LS Handshake Protocol
El Protocolo de Apretón de Manos TLS permite que el cliente y el servidor se autentiquen mutuamente y seleccionen un algoritmo de cifrado y claves criptográficas antes del intercambio de datos por parte del protocolo de aplicación.

Pretty Good Privacy (PGP)
A menudo se utiliza para la compresión de datos, firma digital, cifrado y descifrado de mensajes, correos electrónicos, archivos y directorios, y para mejorar la privacidad de las comunicaciones por correo electrónico. El algoritmo utilizado para el cifrado de mensajes es RSA para el transporte de claves e IDEA para el cifrado masivo de mensajes. PGP utiliza RSA para calcular firmas digitales y MD5 para calcular resúmenes de mensajes.

GNU Privacy Guard (GPG)
Es un software que reemplaza a PGP y una implementación libre del estándar OpenPGP, utilizado para cifrar y descifrar datos. GPG también se conoce como un programa de cifrado híbrido, ya que utiliza criptografía de clave simétrica y asimétrica para mejorar la velocidad y la seguridad del intercambio de claves, lo que se logra utilizando la clave pública del receptor para cifrar la clave de sesión. GPG también es compatible con S/MIME y Secure Shell (SSH). La última versión de GPG admite la mayoría de las funciones criptográficas, como la criptografía de curva elíptica (ECDSA, ECDH y EdDSA), y también es compatible con la biblioteca de criptografía Libgcrypt.

Web of Trust - WOT (Red de Confianza)
Es un modelo de confianza de sistemas accesibles para PGP, OpenPGP y GnuPG. Se trata de una idea que busca descentralizar la distribución de claves entre los usuarios de PGP

**Ciphertext-only Attack**
El atacante solo tiene acceso a una colección de textos cifrados. Esto es mucho más probable que el texto plano conocido, pero también es el más difícil. El ataque es completamente exitoso si se pueden deducir los textos planos correspondientes (o mejor aún, la clave).

**▪ Adaptive Chosen-plaintext Attack**
El atacante tiene acceso completo al mensaje de texto plano, incluido su cifrado, y también puede modificar su contenido mediante una serie de consultas interactivas, seleccionando los bloques de texto plano subsiguientes basándose en la información de las consultas y funciones de cifrado anteriores.

 Chosen-plaintext Attack**
 En este ataque, el atacante obtiene los textos cifrados correspondientes a un conjunto de textos planos de su elección. Esto le permite intentar obtener la clave utilizada y, por lo tanto, descifrar otros mensajes cifrados con esa clave.

Related-Key Attack**
El ataque requiere que las claves diferentes estén estrechamente relacionadas, por ejemplo, en un entorno inalámbrico, donde las claves posteriores podrían derivarse de las anteriores. En ese caso, aunque las claves sean diferentes, son similares. Al igual que el ataque de solo texto cifrado, este tipo de ataque probablemente solo produzca una ruptura parcial.

Dictionary Attack
En este ataque, el atacante construye un diccionario de texto plano junto con su correspondiente texto cifrado, que ha analizado y obtenido durante un período determinado. Tras construir el diccionario, si el atacante obtiene el texto cifrado, utiliza el diccionario ya creado para encontrar el texto plano correspondiente

Known-plaintext Attack**
En este ataque, la única información disponible para el atacante son algunos bloques de texto plano junto con el texto cifrado correspondiente y el algoritmo utilizado para cifrar y descifrar el texto. Con esta información, se deduce la clave utilizada para generar el texto cifrado y así descifrar otros mensajes. 

▪ Chosen-ciphertext Attack: El atacante obtiene los textos planos correspondientes a un conjunto arbitrario de textos cifrados que él mismo eligió

▪ Rubber Hose Attack : Los atacantes extraen secretos criptográficos de una persona mediante coacción o tortura.

▪ Chosen-key Attack : En este tipo de ataque, un atacante no solo rompe un cifrado, sino que también compromete un sistema más grande que depende de ese cifrado. El atacante generalmente rompe un cifrado con una clave de _n_ bits en aproximadamente 2 ^n/2 operaciones.

▪ Timing Attack : El atacante intenta romper el cifrado analizando el tiempo que tarda en ejecutarse el algoritmo de cifrado o descifrado para diferentes entradas

▪ Man-in-the-Middle Attack: un atacante intercepta la comunicación entre un cliente y un servidor y negocia los parámetros criptográficos. Usando este ataque, el atacante puede descifrar el contenido cifrado y obtener información confidencial como contraseñas del sistema

Code Breaking Methodologies 
▪ Brute Force: búsqueda exhaustiva, en la que se determinan las claves probando **todas las combinaciones posibles de caracteres**.

 
▪ Frequency Analysis : Funciona bajo el principio de que, en cualquier segmento de un idioma escrito, ciertas letras y combinaciones de letras aparecen con diferentes frecuencias.

▪ Trickery and Deceit:  El engaño y la manipulación requieren un alto nivel de habilidades matemáticas y criptográficas. Este tipo de ataque **implica el uso de técnicas de ingeniería social para extraer claves criptográficas**.

▪ One-Time Pad:  contiene principalmente un conjunto de letras o números que no se repiten, seleccionados de forma aleatoria por el sistema. El usuario escribe estos valores en pequeñas hojas de papel que luego se pegan juntas formando un bloc o cuaderno.

Birthday Attack:  Un ataque de cumpleaños (birthday attack) se refiere a una clase de ataques de fuerza bruta contra funciones hash criptográficas que hace que la fuerza bruta sea más fácil de realizar. Este ataque se basa en la **paradoja del cumpleaños**, que es la probabilidad de que dos o más personas en un grupo de 23 compartan el mismo cumpleaños

Meet-in-the-Middle Attack on Digital Signature Schemes : es el mejor método de ataque para algoritmos criptográficos que utilizan múltiples claves para el cifrado. utiliza un intercambio espacio-tiempo; también es un tipo de ataque de cumpleaños porque aprovecha las matemáticas detrás de la paradoja del cumpleaños, y consume menos tiempo que un ataque exhaustivo

Side-Channel Attack : ataque físico realizado sobre un dispositivo criptográfico o criptosistema para obtener información sensible.

Hash Collision Attack: Un ataque de colisión de hash se realiza encontrando dos mensajes de entrada diferentes que generan el mismo valor de hash.

DUHK Attack : es una vulnerabilidad criptográfica que permite a los atacantes obtener claves de cifrado usadas para asegurar VPNs y sesiones web.afecta principalmente a cualquier hardware o software que utilice el Generador de Números Aleatorios ANSI X9.31 (RNG)

DROWN Attack: grave vulnerabilidad que puede afectar protocolos criptográficos importantes como HTTPS y otros servicios criptográficos que dependen de SSL y TLS.

Ataque de Tabla Arcoíris: En un ataque de tabla arcoíris, el atacante crea previamente una tabla con todas las posibles contraseñas y sus valores hash correspondientes, llamada tabla arcoíris.

Related-Key Attack : os atacantes lanzan un ataque de clave relacionada explotando la relación matemática entre las claves en un cifrado para obtener acceso a las funciones de encriptación y desencriptación.

Padding Oracle Attack : los atacantes explotan la validación del relleno de un mensaje cifrado para descifrar el texto cifrado. Este tipo de ataque también se conoce como ataque de Vaudenay. Este ataque se realiza principalmente en algoritmos que operan en modo CBC (Cipher Block Chaining)

Attacks on Blockchain 
▪ 51% Attack: ocurre cuando un atacante o grupo de atacantes obtiene el control de más del 50% del poder computacional (tasa de hash) o poder de participación (staking) en una red blockchain.

▪ Finney Attack: tipo de ataque en blockchain que implica que un atacante aproveche los retrasos temporales entre la transmisión y la confirmación de transacciones en redes de criptomonedas para revertir las transacciones antes de que sean confirmadas.

▪ Eclipse Attack: es un tipo de ataque en blockchain en el que un atacante aísla un nodo objetivo del resto de la red al rodearlo con nodos maliciosos, controlando así efectivamente la visión que tiene el nodo sobre la blockchain.

▪ Race Attack: es un ataque de doble gasto que aprovecha el retraso en la confirmación de transacciones en redes blockchain para obtener bienes o servicios sin pagarlos realmente, gastando efectivamente la misma moneda dos veces.

▪ DeFi Sandwich Attack: apunta a intercambios descentralizados (DEXs) y creadores de mercado automatizados (AMMs) para manipular la dinámica del mercado. En este ataque, el atacante explota el retraso en el tiempo y los mecanismos de ejecución de órdenes en los DEX para manipular el precio de un token a su favor.
