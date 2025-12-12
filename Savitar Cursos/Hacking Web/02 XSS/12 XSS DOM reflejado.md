Las vulnerabilidades de DOM reflejado ocurren cuando la aplicación del servidor procesa datos de una solicitud y los repite en la respuesta. Un script en la página procesa los datos reflejados de forma insegura, escribiéndolos finalmente en un receptor peligroso


En este ejercicio vemos que se utiliza la función eval de JS la cual es muy peligrosa y vemos que la pagina hace un petición extra para extraer los valores y reflejar los en la pagina esto lo hace mediante u script que evalúa el valor del parámetro introducido 
```
function search(path) {
    var xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
            eval('var searchResultsObj = ' + this.responseText);
            displaySearchResults(searchResultsObj);
        }
    };
    xhr.open("GET", path + window.location.search);
    xhr.send();
```

Al entrar en burp suit e identificar la petición que se hace a eta función vemos que devuelve en jso donde  searchTerm toma el valor que enviamos por parámetros el cual intentaremos modificar su estructura la no esta sanitizada la entrada y nos aprovechamos de que la función utiliza la función eval para evaluar la expreción que insertemos por lo que al pasar por el input  esto ejecutara el alert en el sitio
```
prueba\"-alert(0)}//
```

```
{"results":[],"searchTerm":"prueba\\"-alert(0)}//"}
```

