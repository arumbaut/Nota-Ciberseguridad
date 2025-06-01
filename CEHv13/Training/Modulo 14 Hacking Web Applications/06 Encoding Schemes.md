**Encoding Schemes**

La codificación es el proceso de convertir información de origen en su forma simbólica equivalente, lo cual ayuda a ocultar el significado de los datos. En el extremo receptor, los datos codificados se decodifican al formato de texto plano. La decodificación es el proceso inverso a la codificación.

**▪ URL Encoding**

La codificación de URL es el proceso de convertir una URL en un formato ASCII válido, de modo que los datos puedan ser transportados de forma segura a través del protocolo HTTP.La codificación de URL reemplaza los caracteres ASCII inusuales con un signo de "%" seguido del código ASCII del carácter expresado en formato hexadecimal de dos dígitos.

**Por ejemplo:**

Espacio ( ) → %20

Comillas (") → %22

Signo de número (#) → %23

Porcentaje (%) → %25

**▪ HTML Encoding**

Un esquema de codificación HTML se utiliza para representar caracteres inusuales de manera que puedan combinarse de forma segura dentro de un documento HTML. La codificación HTML reemplaza caracteres inusuales con cadenas que pueden ser reconocidas, mientras que otros caracteres definen la estructura del documento.

Se definen varias entidades HTML para representar caracteres particularmente comunes, como:

& → &

< → <

> → >

▪ Unicode Encoding Unicode encoding is of two types: 
16-bit Unicode encoding and UTF-8. 
o 16-bit Unicode Encoding
It replaces unusual Unicode characters with "%u" followed by the character’s Unicode codepoint expressed in the hexadecimal format.
• %u2215 /
**o UTF-8**
It is a variable-length encoding standard that expresses each byte in the hexadecimal format and prefixes it with %.
• %c2%a9 © 
• %e2%89%a0 

**▪ Base64 Encoding**
cake = 01100011011000010110101101100101 

Base64 Encoding: 01011001 00110010 01000110 01110010 01011010 01010001 00111101 00111101

**▪ Hex Encoding**

**Hello** 48 65 6C 6C 6F
**Jason** 4A 61 73 6F 6E

