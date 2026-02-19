- Tags : #jwt #enumeration #exploit #enumeration_jwt #enumeration_jwt 

 **Recurso SKF-LABS**: [https://github.com/blabla1337/skf-labs](https://github.com/blabla1337/skf-labs)

Los **Json Web Tokens** (**JWT**) son un tipo de token utilizado en la **autenticación** y **autorización** de usuarios en aplicaciones web. JWT es un estándar abierto (**RFC 7519**) que define un formato compacto y seguro para transmitir información entre diferentes partes de forma confiable.

En lo que respecta a la fase de enumeración y explotación de un JWT, esto se produce cuando un atacante es capaz de obtener información sobre los JWT que se utilizan en la aplicación, lo que podría permitir al atacante explotar las debilidades en la autenticación y autorización de la aplicación.

La enumeración de los JWT se produce cuando un atacante utiliza técnicas de fuerza bruta o cierta ingeniería inversa para obtener información sobre los JWT utilizados por la aplicación web. Por ejemplo, el atacante podría intentar adivinar los valores de los JWT mediante la construcción de **tokens falsos**, tratando de validar en todo momento si la aplicación web los acepta o no. Si el atacante tiene éxito en la enumeración de un JWT válido, podría obtener información confidencial, como nombres de usuario, contraseñas, roles de usuario y otros datos de autenticación y autorización.

La explotación de los JWT se produce cuando un atacante utiliza la información obtenida de la enumeración del JWT para explotar debilidades en la aplicación. Por ejemplo, si la aplicación web utiliza JWT para la autenticación, pero no valida adecuadamente la **firma** del JWT, un atacante podría falsificar el token y acceder a la aplicación web como si fuera un usuario legítimo.

Para prevenir la enumeración y explotación de los JWT, es importante utilizar prácticas seguras de desarrollo web, como la validación adecuada de las solicitudes de entrada, la gestión segura de las claves de firma JWT y la limitación del tiempo de expiración de los JWT.

A continuación, se os proporciona el enlace directo al proyecto de Github SKF-LABS, el cual estaremos usando para practicar la enumeración y explotación de los JWT:

- **SKF-LABS**: [https://github.com/blabla1337/skf-labs](https://github.com/blabla1337/skf-labs)

Los token jwt tiene 3 partes separadas por . en el token Ej 

asdasd89129hcuas9.oiashoiash0127443bv.23872934238y234

La primera parte es el HEADER
La segunda parte es el payload que puede arrastrar propiedades que identifiquen al usuario 
La tercera parte y ultima corresponde al signature [firma digital], se encarga de verificar la integridad del token para evitar manipulaciones y modificaciones.

Podemos ver el token en jwt.io

Si por algún motivo el sitio acepta a nivel algoritmo NONE pues no sera necesario enviar en el toque la sección de signature por lo que pudiéramos manipular el  token.

Cabecera
![](../../../attachments/Pasted%20image%2020260218132101.png)
Aquí construimos la primera parte del token que no es mas que la data en base 64, para concatenarlo con la segunda parte manipulada para acceder a otro usuario.

Payload modificando el id para acceder a la session de otro usuario 
![](../../../attachments/Pasted%20image%2020260218132431.png)

Luego concatenamos los 2 resultado para conformar el toquen completo

![](../../../attachments/Pasted%20image%2020260218132540.png)

Se  deben separa por puntos aunque no se agregue la sección de signature
![](../../../attachments/Pasted%20image%2020260218132751.png)

En caso de ser requerido el campo signature la opción que tenemos es adivinar el secreto o hacer una fuerza bruta del secreto y si este no es muy complejo podríamos obtener un token valido. es decir si descubrimos el secreto pues generariamos un token valido

![](../../../attachments/Pasted%20image%2020260218133649.png)