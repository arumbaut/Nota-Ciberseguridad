**HASH**
Las funciones hash calculan una representación única de tamaño fijo en bits, llamada resumen de mensaje, de cualquier bloque de información arbitrario. Las funciones de resumen de mensaje destilan la información contenida en un archivo (pequeño o grande) en un único número de longitud fija, típicamente entre 128 y 256 bits. Si se cambia cualquier bit de entrada de la función, cada bit de salida tiene un 50% de probabilidad de cambiar.

Los algoritmos de resumen de mensaje en sí no participan en operaciones de cifrado y descifrado. Permiten la creación de firmas digitales y códigos de autenticación de mensajes (MACs), así como la derivación de claves de cifrado a partir de frases de paso. **El papel principal de una función hash criptográfica es proporcionar integridad en la gestión de documentos.**

![](attachments/image20250522233325.png)

**Message Digest Functions**

| **Algoritmo**  | **Tamaño de salida (bits)** | **Tamaño del estado interno (bits)** | **Tamaño del bloque (bits)** | **Tamaño máx. del mensaje (bits)** | **Rondas** | **Operaciones**                    | **Seguridad (bits)** | **Áreas de aplicación (traducidas)**                               |
| -------------- | --------------------------- | ------------------------------------ | ---------------------------- | ---------------------------------- | ---------- | ---------------------------------- | -------------------- | ------------------------------------------------------------------ |
| **MD2**        | 128                         | 128                                  | 128                          | 2⁶⁴                                | 18         | Permutación, Sustitución           | Lógica               | Aplicaciones heredadas, validación de suma de verificación         |
| **MD4**        | 128                         | 128                                  | 512                          | 2⁶⁴                                | 48         | Operaciones (AND, OR, XOR)         | Lógica               | Obsoleto, funciones hash criptográficas tempranas                  |
| **MD5**        | 128                         | —                                    | —                            | —                                  | —          | —                                  | —                    | Verificación de archivos, suma de verificación, firmas digitales   |
| **MD6**        | 224, 256, 384, 512          | 1024                                 | 512                          | Ilimitado                          | Variable   | Operaciones (AND, OR, XOR)         | —                    | Aplicaciones criptográficas, integridad de datos                   |
| **SHA-0**      | 160                         | 128                                  | 512                          | 2⁶⁴                                | 64         | Operaciones (AND, OR, XOR)         | Lógica               | Obsoleto, reemplazado por SHA-1                                    |
| **SHA-1**      | 160                         | 160                                  | 512                          | 2⁶⁴                                | 80         | Operaciones lógicas bit a bit      | —                    | Sistemas heredados, actualizaciones de software, TLS               |
| **SHA-2**      | 224, 256, 384, 512          | 256, 512                             | 512, 1024                    | 2¹²⁸                               | 64, 80     | Operaciones (AND, OR, XOR)         | 112–256              | Aplicaciones seguras, firmas digitales, SSL                        |
| **SHA-3**      | 224, 256, 384, 512          | 1600                                 | 1088, 576                    | Ilimitado                          | Variable   | Construcción esponja (Sponge)      | 112–256              | Aplicaciones seguras, funciones criptográficas de nueva generación |
| **RIPEMD-160** | 160                         | 160                                  | 512                          | 2⁶⁴                                | 160        | Operaciones lógicas (AND, OR, XOR) | 80                   | Aplicaciones criptográficas, integridad de datos                   |
| **WHIRLPOOL**  | 512                         | 512                                  | 512                          | 2²⁵⁶                               | 10         | Operaciones de matriz, sustitución | 256                  | Hash seguro, aplicaciones criptográficas                           |
| **Tiger**      | 192                         | 192                                  | 512                          | Ilimitado                          | 24         | Operaciones lógicas (AND, OR, XOR) | 192                  | Aplicaciones de alta velocidad, validación de suma de verificación |
| **BLAKE2**     | 256, 512                    | 256, 512                             | 512, 1024                    | Ilimitado                          | 10–14      | Operaciones lógicas (AND, OR, XOR) | 128–256              | Hashing de alta velocidad, aplicaciones seguras                    |
| **BLAKE3**     | 256                         | 256                                  | 512                          | Ilimitado                          | Variable   | Operaciones lógicas (AND, OR, XOR) | 128                  | Aplicaciones criptográficas de alto rendimiento                    |

**Función de Resumen de Mensaje: MD5 y MD6**  
**MD2**

Es compatible con máquinas de 8 bits, mientras que MD4 y MD5 son compatibles con máquinas de 32 bits.  
El algoritmo rellena el mensaje con bits adicionales para garantizar que el número de bits sea divisible por 512.  
Los bits adicionales pueden incluir un mensaje binario de 64 bits.  
Los ataques a versiones de MD4 se han vuelto cada vez más exitosos.  
Las investigaciones han demostrado cómo un atacante puede lanzar ataques de colisión contra la versión completa de MD4 en menos de un minuto en una PC típica.

**MD5** es ligeramente más seguro, pero es más lento que MD4.  
Sin embargo, tanto el tamaño del resumen de mensaje como los requisitos de relleno siguen siendo los mismos.  
MD5 es una función hash criptográfica ampliamente utilizada que toma un mensaje de longitud arbitraria como entrada y produce una huella digital o resumen de mensaje de 128 bits (16 bytes) como salida.  
MD5 puede utilizarse en una amplia variedad de aplicaciones criptográficas y es útil para aplicaciones de firma digital, verificación de integridad de archivos y almacenamiento de contraseñas.  
Sin embargo, MD5 no es resistente a colisiones; por lo tanto, es mejor usar los algoritmos más recientes, como MD6, SHA-2 y SHA-3.

**MD6** 

Utiliza una estructura similar a un árbol de Merkle para permitir el cálculo paralelo a gran escala de hashes para entradas muy largas.

**Message Digest Function: Secure Hashing Algorithm (SHA)**

Es similar a la familia de funciones hash del algoritmo de resumen de mensajes. Es ligeramente más lento que MD5, pero su mayor tamaño de resumen lo hace más seguro contra ataques de colisión e inversión por fuerza bruta

El cifrado SHA es una serie de cinco funciones criptográficas diferentes, y actualmente tiene tres generaciones: SHA-1, SHA-2 y SHA-3.

**▪ SHA-1:** Es una función hash de 160 bits que se asemeja al antiguo algoritmo MD5 desarrollado por Ron Rivest. Produce un resumen de 160 bits a partir de un mensaje con una longitud máxima de (2⁶⁴ − 1) bits. Fue diseñada por la Agencia de Seguridad Nacional (NSA) para formar parte del Algoritmo de Firma Digital (DSA). Se utiliza comúnmente en protocolos de seguridad como PGP, TLS, SSH y SSL. Desde 2010, SHA-1 ya no está aprobada para su uso criptográfico debido a sus debilidades criptográficas.

**▪ SHA-2:** SHA-2 es una familia de dos funciones hash similares con diferentes tamaños de bloque, a saber, SHA-256, que utiliza palabras de 32 bits, y SHA-512, que utiliza palabras de 64 bits. Las versiones truncadas de cada estándar son SHA-224 y SHA-384.

**▪ SHA-3:** SHA-3 utiliza una construcción de esponja en la que los bloques de mensaje se combinan con una operación XOR en los bits iniciales del estado, los cuales luego son permutados de manera reversible por el algoritmo. Soporta los mismos tamaños de hash que SHA-2, pero difiere considerablemente en su estructura interna del resto de la familia SHA.

**Hardware-Based Encryption**

Types of hardware encryption devices

**▪ TPM**

El Módulo de Plataforma Confiable (TPM, por sus siglas en inglés) es un criptoprocesador o chip que está presente en la placa base. Puede almacenar de forma segura las claves de cifrado y realizar muchas operaciones criptográficas. El TPM ofrece varias funciones, como autenticar la integridad de la plataforma, proporcionar capacidades de cifrado de disco completo, realizar almacenamiento de contraseñas y brindar protección de licencias de software.

**▪ HSM**

Un módulo de seguridad de hardware (HSM, por sus siglas en inglés) es un dispositivo de seguridad externo adicional que se utiliza en un sistema para el cripto-procesamiento, y puede utilizarse para gestionar, generar y almacenar de forma segura claves criptográficas. El HSM ofrece un procesamiento de cifrado mejorado que es útil para claves simétricas de más de 256 bits. Los dispositivos HSM de alto rendimiento se conectan a la red mediante TCP/IP. Algunos dispositivos HSM incluyen Thales Luna Network HSM, nShield HSM, Utimaco HSM y Cryptosec Dekaton PCI.

**▪ USB Encryption**

El cifrado USB es una función adicional para los dispositivos de almacenamiento USB, que ofrece servicios de cifrado integrados. Los dispositivos USB cifrados necesitan un sistema de credenciales en el dispositivo o credenciales basadas en software o hardware desde una computadora. El cifrado USB proporciona protección contra la distribución de malware a través de USB y ayuda a prevenir la pérdida y fuga de datos. Algunos dispositivos USB cifrados por hardware incluyen Encrypted USB, Kingston Ironkey D300S y diskAshur Pro.

**▪ Hard Drive Encryption**

La cifrado de disco duro es una tecnología mediante la cual los datos almacenados en el hardware pueden ser cifrados utilizando una amplia variedad de opciones de cifrado. Los dispositivos de cifrado de disco duro no pueden usar un teclado integrado ni un lector de huellas dactilares; en su lugar, requieren un TPM (módulo de plataforma confiable) o un HSM (módulo de seguridad de hardware). Estos dispositivos pueden instalarse como un disco interno en una computadora. Algunos dispositivos de cifrado de disco duro incluyen el cifrado de hardware AES de grado militar de 256 bits y el DiskCypher AES Sata Hard Drive Encryption.




