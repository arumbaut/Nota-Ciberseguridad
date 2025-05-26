
🔐**Cryptography**

La criptografía permite asegurar transacciones, comunicaciones y otros procesos realizados en el mundo electrónico. El cifrado es el proceso de convertir texto plano legible en texto cifrado ilegible utilizando un conjunto de algoritmos complejos que transforman los datos en bloques o flujos de caracteres alfanuméricos aleatorios.algoritmos de cifrado como \[**DES, AES, RC4, RC5, RC6, DSA, RSA, MD5, SHA**]

**Objectives of Cryptography** 

**▪ Confidentiality:** Garantía de que la información sea accesible solo para aquellas personas autorizadas a acceder a ella.

**▪ Integrity:** Confiabilidad de los datos o recursos en términos de prevención de cambios inapropiados y no autorizados.

**▪ Authentication:** Garantía de que la comunicación, documento o dato es genuino..

**▪ Nonrepudiation:** Garantía de que el remitente de un mensaje no pueda negar posteriormente haber enviado el mensaje y que el receptor no pueda negar haberlo recibido.

#### Cryptography Process

![](attachments/image20250522180122.png)

#### :TiShieldLock: Types of Cryptography

##### ▪ Symmetric Encryption

El cifrado simétrico requiere que tanto el remitente como el receptor del mensaje posean la misma clave de cifrado. El remitente utiliza una clave para cifrar el texto plano y envía el texto cifrado resultante al destinatario, quien utiliza la misma clave (utilizada para el cifrado) para descifrar el texto cifrado en texto plano. El cifrado simétrico también se conoce como criptografía de clave secreta

![](attachments/image20250522180615.png)

##### ▪ Asymmetric Encryption

==El concepto de cifrado asimétrico (conocido como criptografía de clave pública)== se introdujo para resolver los problemas de gestión de claves. El cifrado asimétrico **implica tanto una clave pública como una clave privada**. La clave pública está disponible públicamente, mientras que el remitente mantiene la clave privada en secreto. Un sistema de clave asimétrica es un método de cifrado que utiliza un par de claves compuesto por una clave pública disponible para cualquiera y una clave privada mantenida solo por el propietario de la clave, lo que ayuda a **proporcionar confidencialidad, integridad, autenticación y no repudio en la gestión de datos.**

![[image20250522180952.png]]

|   |   |   |
|---|---|---|
|**Método Criptográfico**|**Fortalezas**|**Debilidades**|
|**Cifrado Simétrico**|- Más rápido y fácil de implementar, ya que se utiliza la misma clave para cifrar y descifrar los datos.  <br>- Requiere menos potencia de procesamiento.  <br>- Puede implementarse en chips integrados específicos (ASIC).  <br>- Previene el compromiso generalizado de la seguridad de los mensajes, ya que se utilizan claves secretas diferentes para comunicarse con diferentes partes.  <br>- La clave no está vinculada a los datos transferidos en el enlace; por lo tanto, incluso si los datos son interceptados, no es posible descifrarlos.|- Falta de un canal seguro para intercambiar la clave secreta.  <br>- Difícil de gestionar y asegurar demasiadas claves compartidas que se generan para comunicarse con diferentes partes.  <br>- No proporciona garantía sobre el origen y la autenticidad de un mensaje, ya que la misma clave es utilizada por el remitente y el receptor.  <br>- Vulnerable a ataques de diccionario y ataques de fuerza bruta.|
|**Cifrado Asimétrico**|- Conveniente de usar, ya que no se requiere la distribución de claves para cifrar mensajes.  <br>- Mayor seguridad, ya que no es necesario compartir ni transmitir claves privadas a nadie.  <br>- Proporciona firmas digitales que no pueden ser repudiadas.|- Lento en el procesamiento y requiere alta potencia de procesamiento.  <br>- Es posible un compromiso generalizado de la seguridad del mensaje (es decir, un atacante puede leer mensajes completos si la clave privada es comprometida).  <br>- Los mensajes recibidos no pueden ser descifrados si se pierde la clave privada.  <br>- Vulnerable a ataques de intermediario (man-in-the-middle) y ataques de fuerza bruta.|

##### Government Access to Keys (GAK)

El Acceso del Gobierno a las Claves (GAK, por sus siglas en inglés) se refiere a la obligación legal de individuos y organizaciones de revelar sus claves criptográficas a las agencias gubernamentales. Esto significa que las empresas de software deben entregar copias de todas las claves (o al menos una parte suficiente de la clave para que el resto pueda ser descifrado) al gobierno

**Ciphers**

En criptografía, un cifrado es un algoritmo (una serie de pasos bien definidos) para realizar la encriptación y desencriptación. El cifrado es el proceso de convertir texto plano en un cifrado o código; el proceso inverso se llama descifrado. Un mensaje encriptado mediante un cifrado se vuelve ilegible a menos que su receptor conozca la clave secreta necesaria para descifrarlo

Los algoritmos de cifrado pueden ser de código abierto (el proceso algorítmico está en el dominio público mientras que la clave es seleccionada por el usuario y es privada) o de código cerrado (el proceso se desarrolla para su uso en dominios específicos, como el militar, y el algoritmo en sí no está en el dominio público)

#### Types of ciphers 
##### ▪ Classical Ciphers

**Tipos de cifrados clásicos**

**Sustitution cipher**: El usuario reemplaza unidades del texto plano por texto cifrado de acuerdo con un sistema regular. Las unidades pueden ser letras individuales, pares de letras o combinaciones de las mismas, etc. El receptor realiza una sustitución inversa para descifrar el texto. Ejemplos incluyen el cifrado de Beale, el cifrado autoclave, el cifrado de Gronsfeld y el cifrado de Hill.  
Por ejemplo, “HELLO WORLD” puede ser encriptado como “PSTER HGFST” (es decir, H=P, E=S, etc.).

**Transposition cipher**: Aquí, las letras del texto plano se reorganizan de acuerdo con un sistema regular para producir el texto cifrado. Por ejemplo, “CRYPTOGRAPHY” al ser encriptado se convierte en “AOYCRGPTYRHP.” Ejemplos incluyen el cifrado de cerca de rieles (rail fence cipher), el cifrado de ruta (route cipher) y la transposición de Myszkowski.

##### ▪ Modern Ciphers

**Based on the type of key used**

• Symmetric-key algorithms (Private-key cryptography): Use the same key for encryption and decryption.

• Asymmetric-key algorithms (Public-key cryptography): Use two different keys for encryption and decryption.

**Based on the type of input data**

**• Block cipher:** Algoritmos deterministas que operan sobre un bloque (un grupo de bits) de tamaño fijo con una transformación invariable especificada por una clave simétrica. La mayoría de los cifrados modernos son cifrados por bloques. Se utilizan ampliamente para cifrar grandes cantidades de datos. **Ejemplos incluyen DES, AES, IDEA, etc.** Cuando el tamaño del bloque es menor que el utilizado por el cifrado, se emplea un relleno para lograr un tamaño de bloque fijo.

**•** **(Flujo)****Stream cipher:** Cifrados de clave simétrica en los que los dígitos de texto plano se combinan con un flujo de clave (flujo de dígitos cifrados seudoaleatorios). Aquí, el usuario aplica la clave a cada bit, uno a la vez. Ejemplos incluyen RC4, SEAL, etc.

## Subnotas
- [[1.1 Symmetric Encryption Algorithms]]
- [[1.2 Asymmetric Encryption Algorithms]]
