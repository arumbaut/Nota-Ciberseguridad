Acontece cuando una web en algún punto de entrada de datos muestra el contenido sin ser previamente sanitizado. Esto nos permite introducir código JavaScript pudiendo inyectar código malicioso .

Se conoce como XSS reflejado porque simplemente se refleja en la web lo que introducimos
Ej
```
<script>alert('Hola...') </script>
```

Al introducir este código en un input si no esta correctamente sanitizado pues nos genera un cuadro de dialogo con el msg.

Vale destacar que si bien parece inofensivo al enviar un enlace del sitio vulnerable con el código malicioso introducido podríamos generar problemas a esos usuario pudiendo llegar a robar las cookies o mas
Ej:
```
https://0a0f00ac038093e4807f994f001000ca.web-security-academy.net/?search=%3Cscript%3Ealert%28%27asdasd%27%29%3C%2Fscript%3E
```

Pudiéramos llegar a extraer las cookies pasando este código malicioso
```
<script>alert(document.cookie)</script>
```