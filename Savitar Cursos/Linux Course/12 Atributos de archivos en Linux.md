- Tags: #atributos #linux #files_system

En Linux, además de los permisos normales de lectura/escritura (`chmod`), existen los **atributos de archivo**. `chattr` (_Change Attribute_) se encarga de modificarlos a nivel del sistema de archivos (Ext4, por ejemplo).

Además del atributo `i` (inmutable), hay varios otros que son extremadamente útiles para la seguridad y la administración.

### 1. El atributo `a` (Append Only)

Este es oro puro para la **auditoría y logs**.

- **Qué hace:** Solo permite **añadir** texto al final del archivo. Nadie (ni `root`) puede borrar ni modificar lo que ya está escrito.
    
- **Uso común:** Archivos de log (`/var/log/auth.log`). Si un atacante entra, no podrá borrar las huellas de lo que hizo, solo podrá "escribir encima" si el archivo no está protegido, pero con `+a` solo puede añadir más líneas.
    
- **Comando:** `sudo chattr +a archivo.log`
    

### 2. El atributo `s` (Secure Deletion)

- **Qué hace:** Cuando borras el archivo, los bloques en el disco se sobrescriben con ceros inmediatamente.
    
- **Uso común:** Archivos con claves privadas o contraseñas sensibles. Evita que alguien use herramientas de recuperación de datos (como `testdisk` o `photorec`) para recuperar el archivo borrado.
    
- **Comando:** `sudo chattr +s claves.txt`
    

### 3. El atributo `c` (Compressed)

- **Qué hace:** El kernel comprime automáticamente el archivo en el disco y lo descomprime al leerlo.
    
- **Uso común:** Ahorrar espacio en archivos muy grandes que no se usan seguido.
    
- **Comando:** `sudo chattr +c archivo_gigante.dat`
    

### 4. El atributo `e` (Extents)

- **Qué hace:** Indica que el archivo está usando "extents" para gestionar bloques grandes de datos. Casi todos los archivos en sistemas modernos lo tienen por defecto. No se suele cambiar a mano.
    
### 5. El atributo `i` (Inmutable)
---
La `i` significa **Inmutable**. Al aplicar este atributo:

- **Qué hace:** Bloquea el archivo por completo. Nadie (ni siquiera `root`) puede borrarlo, modificarlo, renombrarlo o crear enlaces hacia él.
    
- **Uso común:** Proteger archivos críticos como `/etc/resolv.conf`, `/etc/passwd` o binarios del sistema para evitar alteraciones maliciosas.
    
- **Comando:** `sudo chattr +i /etc/resolv.conf`
### ¿Cómo ver qué atributos tiene un archivo?

Para ver estos atributos no usas `ls -l`, sino el comando **`lsattr`**:

Bash

```
lsattr /etc/resolv.conf
```

Si ves una `i`, el candado está puesto. Si ves una `a`, es de solo anexar.

### Resumen para tu "Cheat Sheet" de Junior:

|**Atributo**|**Significado**|**Efecto Principal**|
|---|---|---|
|**`i`**|Inmutable|No se puede tocar, borrar ni renombrar.|
|**`a`**|Append|Solo se puede escribir al final (ideal para logs).|
|**`s`**|Secure|Borrado físico real del disco (anti-forense).|
|**`c`**|Compress|Compresión transparente por el kernel.|