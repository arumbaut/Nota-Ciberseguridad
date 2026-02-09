- Tags : #recursos_github 
El ataque **Prototype Pollution** es una técnica de ataque que aprovecha las vulnerabilidades en la implementación de objetos en JavaScript. Esta técnica de ataque se utiliza para modificar la propiedad “**prototype**” de un objeto en una aplicación web, lo que puede permitir al atacante ejecutar código malicioso o manipular los datos de la aplicación.

En JavaScript, la propiedad “prototype” se utiliza para definir las propiedades y métodos de un objeto. Los atacantes pueden explotar esta característica de JavaScript para modificar las propiedades y métodos de un objeto y tomar el control de la aplicación.

El ataque de Prototype Pollution se produce cuando un atacante modifica la propiedad “prototype” de un objeto en una aplicación web. Esto se puede lograr mediante la manipulación de datos que se envían a través de formularios o solicitudes AJAX, o mediante la inserción de código malicioso en el código JavaScript de la aplicación.

Una vez que el objeto ha sido manipulado, el atacante puede ejecutar código malicioso en la aplicación, manipular los datos de la aplicación o tomar el control de la sesión de un usuario. Por ejemplo, un atacante podría modificar la propiedad “prototype” de un objeto de autenticación de usuario para permitir el acceso a una cuenta sin la necesidad de una contraseña.

El impacto de la explotación del ataque Prototype Pollution puede ser significativo, ya que los atacantes pueden tomar el control de la aplicación o comprometer los datos de los usuarios. Además, dado que el ataque se basa en vulnerabilidades en la implementación de objetos en JavaScript, puede ser difícil de detectar y corregir.

A continuación, se proporciona el enlace directo al proyecto de Github que utilizamos en esta clase para desplegar un entorno vulnerable con el que poder practicar:

- **SKF-LABS**: [https://github.com/blabla1337/skf-labs](https://github.com/blabla1337/skf-labs)
- **Recurso**: [https://medium.com/node-modules/what-is-prototype-pollution-and-why-is-it-such-a-big-deal-2dd8d89a93c](https://medium.com/node-modules/what-is-prototype-pollution-and-why-is-it-such-a-big-deal-2dd8d89a93c)

Cuando en JS una propiedad no existe para el objeto dado esta es buscada en su prototipo 

Ej:
```js
var merge = function(target, source) {
    for(var attr in source) {
        if(typeof(target[attr]) === "object" && typeof(source[attr]) === "object") {
            merge(target[attr], source[attr]);
        } else {
            target[attr] = source[attr];
        }
    }
    return target;
};

var s4vitar = {"name": "Marcelo Vázquez", "age": 27}
var admin = {"name": "Jon Doe", "age": 57, "isAdmin": true}

//Solicitud original
var body = JSON.parse('{"email": "s4vitar@s4vitar.com", "msg": "Hola esto es una prueba"}');

//Solicitud modificada mediante burpsuit
var body = JSON.parse('{"email": "s4vitar@s4vitar.com", "msg": "Hola esto es una prueba","__proto__":{"isAdmin": true}}');

console.log(merge({"ipAddress": "127.0.0.1"}, body));

console.log("¿El usuario admin es administrador?" + admin.isAdmin);

//NO existe la propiedad isAdmin la da undefined
console.log("¿El usuario s4vitar es administrador?" + s4vitar.isAdmin);



```