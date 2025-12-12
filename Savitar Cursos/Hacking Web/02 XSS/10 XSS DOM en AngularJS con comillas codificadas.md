Repo de Multiples Payload
https://github.com/swisskyrepo/PayloadsAllTheThings

AngularJS es una popular biblioteca de JavaScript que escanea el contenido de los nodos HTML que contienen el atributo ng-app (también conocido como directiva de AngularJS). Al añadir una directiva al código HTML, se pueden ejecutar expresiones JavaScript entre llaves dobles. Esta técnica es útil al codificar corchetes angulares.

Este ataque es efectivo cuando el código que introducimos se encuentra dentro de una directiva ng-app

Ej: Al pasar esto pon un input que se refleje en el sitio y al estar dentro de la directiva ng-app Angular lo interpreta como codigo de javascrip y lo ejecuta
```
{{constructor.constructor('alert(1)')()}}
```