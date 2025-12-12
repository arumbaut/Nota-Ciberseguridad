Cuando se hace este tipo de inyección es importante tener en cuenta que el html con nuestra inyeccion no viene de el servidor sino que se construye en nuestro navegador 
Este explota las vulnerabilidades de una mala sanitizacion y la escritura con funciones como document.write y document.location

Ej
Este es el codigo que se ejecuta para escribir en la web
![[Pasted image 20251203103118.png]]
No hay una validacion del parametro query por lo que al pasar por parametro  el siguiente codigo estariamos cerrando la etiqueta img y agregando nuestro codigo malicioso
```

"><svg onload=alert(1)>
```