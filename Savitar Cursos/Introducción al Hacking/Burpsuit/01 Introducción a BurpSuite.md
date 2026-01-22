- Tags : #burpsuit #sqlmap 

Establecer un scope para no recibir en el history info fuera del scope para esto nos vamos a Proxy y marcamos
![[Pasted image 20260113191815.png]] 

Luego vamos a target y le indicamos el dominio o los dominios que queremos en el scope
![[Pasted image 20260113192048.png]]
En la pestaña opciones podemos aplicar sustituciones ademas de decirle que al hacer forward nos capture la respuesta de la petición que por defecto solo captura la request no la response entre otras cosas que se pueden realizar

![[Pasted image 20260113205252.png]]

Plugin de python para copiar las request y llevarla a codigo de python 
**Nombre**: Copy As Python Request

Muchas herramientas permiten indicarle el parametro de proxy para funciona y mediante burpsuit pudieramos ver que esta tramitando la herramient Ej sqlmap
```bash
sqlmap -r reques.req -p uid --batch --dbs --dbms mysql --proxy http//ip:port

Indiacariamos el proxy de burpsuit
```