![[Pasted image 20260105193502.png]]
La letra a en el campo de field indica que el valor es alfanumerico si tine # el valor es de numero clicando en el fiel nos da una lista de valores para ese campo

Hay una diferencie entre status != 200 y NOT status = 200

```
Devuelve eventos donde el campo de estado no es 200

(index=web OR index=security) status != 200


Devuelve todos los eventos que no tienen un campo donde el estado es 200 lo que quiere decir que si el evento no tiene un campo status se incluye en el resultado

(index=web OR index=security) NOT status = 200
```

Alternativas a operadores
```
index=web (status=500 OR status=503 OR status=505)

Alternativa operador IN

index=web status IN ("500","503","505")

```

El comando fields se puede utilizar para incluir o excluir fields
```
Crea una tabla donde se muestra un recuento de eventos segun su status

index=web status IN ("500","503","505")
| fields status      # +status incluye, -status excluye, default +
| stats count by status
```

Comando rename para renombra los nomfres de los fields en nuestra busqueda  y darle mas sentido
```
index=web status IN ("500","503","505")
| fields status      
| stats count by status
| rename status as "HTTP Status", count as "Number Events"
```

Crear cmapos temporales en esplunk para los resultados de las busquedas mediante el comandos como eval , este se utiliza para calcular y manejar los valores de campos
```
index=network sourceype=cisco_wsa_squid
| status sum(sc_bytes) as Bytes by usage 
```

![[Pasted image 20260105200258.png]]

```
index=network sourceype=cisco_wsa_squid
| status sum(sc_bytes) as Bytes by usage 
| eval bandwidth=Bytes/1024/1024
```
Coonvertir los Bytes a MB facilita la lectura del informe

Extraccion de fields
Se pueden utilizar los comandos  | erex y | rex  o con la utilidad de extracción de fields
![[Pasted image 20260105200628.png]]
```
index=games sourcetype=SimCubeBeta
| erex Character fromfield=_raw examples="pixie, Kooby"
| where isnull(Character)
```

Podemos ver la expresion regular que Splunk utiliza para la coincidencia en el Menu Jobs

El comando rex permite usar grups de capturas de expresiones regulares se puede usar en valores de campos  o datos sin procesar, permite buscar coincidencias en varios grupos 
Creamos un grupo User
```
index=games sourcetype=SimCubeBeta
| rex field=_raw "^[^'\n]*'(?P<User>[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9.]+)"
```

Agregamos otro grupo llamado Character
```
index=games sourcetype=SimCubeBeta
| rex field=_raw "^[^'\n]*'(?P<User>[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9.]+)'\s[a-zA-Z:]+'(?P<Character>[a-zA-Z0-9.-]+)"
```