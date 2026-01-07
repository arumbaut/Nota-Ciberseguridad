Splunk Search Language cuenta de 5 componentes

Search Term
Commands : Le dicen a splunk que queremos hacer con los resultados, incluye crear graficos, computr estadisticas y dar formato a la salida (crear tablas)

Function : Explican como queremos graficar y evaluar los resultados
Argumentos : Son las variables que queremos que se apliquen a la funcion
Clauses: Explican como queremos que los datos sean agrupados o definidos

![[Pasted image 20260105120025.png]]

Cuando hacemos as Visits lo que hacemos es guardar el resultado en la fila Visists, al agregar la clausula by cs_username lo que intentamos es dividir el conteo de estos evento por empleados individuales 
Resultado :

![[Pasted image 20260105120602.png]]

El comando searh permite filtrar la salida de nuestras busquedas

![[Pasted image 20260105120251.png]]


![[Pasted image 20260105120648.png]]

Si un comando hace referencia a un valor especifico este valor especifico si es case sensitive por lo que tiene que escribirse igual 

Limitar el tiempo es lo mejor para limitar los datos de busqueda despues de este estan index , source, host, sourctype en ese orden

En las busquedas es generalmente mejor incluir que excluir 