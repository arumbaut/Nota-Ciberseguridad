Atraves de este parametro no se recarga la pagina completa sino una porcion del html pero podemos forzar a intentar cargar algo del servidor y jugar con los errores de respuestas 
Ej
![[Pasted image 20251203105649.png]]
Aquí vemos la función que inserta nuestro texto en el html pues aqui podemos intentar cosas como cargar una imagen en el servidor.
```
<img src="test"/>  

#Esto nos intenta cargar algo que da error y a partir de aqui pues podemos manipular que hacer cuandoocurre un error

<img src=0 onerror=alert("Logrado")> 
#Intenta cargar una imagen y si ocurre algun error pues lanza una alert a partir del evento
```