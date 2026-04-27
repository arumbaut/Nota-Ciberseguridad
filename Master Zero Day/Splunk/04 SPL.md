### Splunk Programing Lenguage

## Campos Claves:

##### Host: 
Equipo donde se producen los eventos

##### Source: 
Identifica la fuente de un evento, de donde proviene. Es decir un servidor de Windows puede tener varios servicios como Servidor Web , AD, Radius . El source especifica que servicio genero el log

##### Time o Timestamp: 
Indica el momento exacto en el que se genero el evento. Si el evento tiene un timestamp que splunk no puede leer pues splunk le agrega como timestamp el  momento en que se indexo a splunk.

##### Index: 
Es el repositorio de datos en si mismo. Estos cumplen 3 funciones principales 
###### Retención - Cuanto tiempo va a estar el log en nuestro sistema. Todos los eventos de un mismo indice tendrán el mismo periodo de retención

###### Control de Acceso: No todos los usuarios necesitan acceder a la misma información.

###### Performance: Al dividir la información en indice y agregar este indice a la query mejora sustancialmente el performance de la búsqueda

##### SourceType:
Identifica la estructura de datos de un evento, determina como splunk formatea los datos durante el periodo de indexado y de búsqueda. Define como se extraen los campos de los logs ingestados.


## Tendremos 2 tipos de búsquedas
Raw event searches: Solo recupera eventos de un indice o indices. Se utilizan normalmente cuando se quiere analizar un problema. SPL: Búsqueda   básicas

![[Pasted image 20260415232339.png|763]]

#### LOGICA BOOLEANA
![[Pasted image 20260415232653.png|883]]

Transforming searches: Son búsquedas que realizan algún tipo de modificación o calculo estadístico sobre un conjunto de resultados.  SPL: Búsqueda básicas | Transformación  |  Transformación o Filtro  