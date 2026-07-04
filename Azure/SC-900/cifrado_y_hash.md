# Descripción del cifrado y el código hash

## Introducción
- Una manera de mitigar las amenazas de ciberseguridad más comunes es cifrar datos confidenciales o valiosos.
- El cifrado es el proceso para hacer que los datos aparezcan ilegibles e inútiles para visores no autorizados.

## Tipos de cifrado

### Cifrado simétrico
- Usa la misma clave para cifrar y descifrar los datos.

### Cifrado asimétrico
- Usa una clave pública y un par de claves privadas.
- Se utiliza para:
  - Acceso a sitios en Internet mediante el protocolo HTTPS.
  - Soluciones de firma de datos electrónicas.

## Cifrado de datos

### Cifrado de datos en reposo
- Los datos en reposo son los datos que se almacenan en un dispositivo físico, como un servidor.
- Pueden estar almacenados en:
  - Una base de datos.
  - Una cuenta de almacenamiento.

### Cifrado de datos en tránsito
- Los datos en tránsito son los que se están moviendo de una ubicación a otra.
- Ejemplo: HTTPS es un ejemplo de cifrado en tránsito.

### Cifrado de datos en uso
- Protege los datos en un almacenamiento no persistente, como:
  - RAM.
  - Memoria caché de CPU.
- Tecnologías utilizadas:
  - Creación de un enclave (como una caja fuerte con llave) que protege los datos y los mantiene cifrados mientras la CPU los procesa.

## Aplicación de algoritmo hash

### ¿Qué es un hash?
- El hash utiliza un algoritmo para convertir el texto en un valor hash de longitud fija único denominado hash.
- Características:
  - Cada vez que se aplica un algoritmo hash al mismo texto mediante el mismo algoritmo, se genera el mismo valor hash.
  - El hash se puede usar como identificador único de los datos asociados.

### Diferencias entre hash y cifrado
- El hash no usa claves.
- El valor al que se aplica el algoritmo hash no se descifra posteriormente en el original.

### Uso del hash
- **Almacenamiento de contraseñas**:
  - Cuando un usuario escribe su contraseña, el mismo algoritmo que creó el hash almacenado genera un hash de la contraseña escrita.
  - Se compara con la versión hash almacenada de la contraseña.
  - Si coinciden, el usuario ha escrito correctamente la contraseña.

### Riesgos del hash
- Las funciones hash son deterministas, lo que significa que los hackers pueden usar:
  - **Ataques de diccionario**.
  - **Ataques de fuerza bruta** mediante el hash de las contraseñas.
- Por cada hash coincidente, obtienen la contraseña real.

### Mitigación de riesgos
- Para reducir este riesgo, a menudo las contraseñas se "cifran con sal".

