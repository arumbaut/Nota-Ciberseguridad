#### **Footprinting**

Este paso actúa como una fase preparatoria para el atacante, quien necesita recopilar la mayor cantidad de información posible para encontrar fácilmente formas de infiltrarse en la red objetivo.

#### **Reconnaissance**

Reconocimiento (también conocido como footprinting) se refiere a la fase preparatoria en la que un atacante busca recopilar la mayor cantidad de información posible sobre un objetivo de evaluación antes de lanzar un ataque.

#### **Types of Footprinting/Reconnaissance**

#### **▪ Passive Footprinting**

Implica recopilar información sobre el objetivo sin interacción directa. Es principalmente útil cuando las actividades de recopilación de información no deben ser detectadas por el objetivo. Solo se puede recopilar información archivada y almacenada sobre el objetivo utilizando motores de búsqueda, sitios de redes sociales, entre otros.

#### **▪ Active Footprinting**

Implica recopilar información sobre el objetivo con interacción directa. En el footprinting activo, el objetivo puede reconocer el proceso de recopilación de información en curso, ya que interactuamos de manera abierta con la red objetivo. Involucra: **Interrogación de DNS, Ingeniería social, Escaneo de redes/puertos,** **Enumeración de usuarios y servicios**

#### **Objetivos del Footprinting:** 
Para desarrollar una estrategia de hacking, los atacantes deben recopilar información sobre la red de la organización objetivo. Posteriormente, utilizan dicha información para identificar la forma más sencilla de vulnerar el perímetro de seguridad de la organización. Como se mencionó anteriormente, la metodología del footprinting facilita la recopilación de información sobre la organización objetivo y desempeña un papel vital en el proceso de hacking. El footprinting proporciona un resumen de la estrategia de seguridad, como la ubicación de firewalls, proxies y otras soluciones de seguridad. Los hackers pueden analizar el informe del footprinting para identificar vulnerabilidades en la estrategia de seguridad de la organización objetivo y desarrollar un plan de hacking en consecuencia. 

#### **Amenazas de Footprinting:**

**▪ Ataques al sistema y a la red:** El footprinting permite a un atacante realizar ataques al sistema y a la red. De esta forma, los atacantes pueden recopilar información relacionada con la configuración del sistema de la organización objetivo, 
**▪ Fuga de información:** La fuga de información representa una amenaza para cualquier organización. Si la información confidencial de una entidad cae en manos de los atacantes, pueden organizar un ataque basándose en ella o, alternativamente, utilizarla para obtener un beneficio económico. 
**▪ Pérdida de privacidad:** Mediante el footprinting, los hackers pueden acceder a los sistemas y redes de la organización e incluso escalar privilegios hasta niveles de administrador, lo que resulta en la pérdida de privacidad para la organización en su conjunto y para su personal.
**▪ Espionaje corporativo:** El espionaje corporativo es una amenaza fundamental para las organizaciones, ya que la competencia suele intentar obtener datos confidenciales mediante footprinting. Con este enfoque, los competidores pueden lanzar productos similares al mercado, modificar precios y, en general, socavar la posición de mercado de la organización objetivo.
**▪ Pérdida empresarial:** El footprinting puede tener un impacto importante en organizaciones como negocios en línea y otros sitios web de comercio electrónico, así como en empresas del sector bancario y financiero. Miles de millones de dólares se pierden cada año debido a ataques maliciosos de hackers.
#### **Footprinting Methodology :**

![](attachments/image20250524225024.png)


|                  |                                                                                                  |                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| **Operador**     | **Descripción**                                                                                  | **Ejemplo**                                                 |
| **site:**        | Restringe los resultados a un sitio o dominio específico.                                        | games site:www.certifiedhacker.com                          |
| **allinurl:**    | Muestra solo páginas que contienen todos los términos en la URL.                                 | allinurl: google career                                     |
| **inurl:**       | Muestra solo páginas que contienen el término especificado en la URL.                            | inurl:copy site:www.google.com                              |
| **intext:**      | Muestra resultados con el término especificado dentro del cuerpo de la página.                   | intext:"vpn configuration"                                  |
| **allintitle:**  | Muestra solo páginas cuyo título contiene todos los términos especificados.                      | allintitle: detect malware                                  |
| **intitle:**     | Muestra solo páginas cuyo título contiene el término especificado.                               | malware detection intitle:help                              |
| **inanchor:**    | Muestra páginas con enlaces cuyo texto de anclaje contiene el término especificado.              | Anti-virus inanchor:Norton                                  |
| **allinanchor:** | Muestra páginas cuyos enlaces contienen todos los términos especificados en el texto de anclaje. | allinanchor: best cloud service provider                    |
| **cache:**       | Muestra la versión en caché de una página almacenada por Google.                                 | cache:www.eff.org                                           |
| **link:**        | Encuentra páginas que enlazan a un sitio o página específica.                                    | link:www.googleguide.com                                    |
| **related:**     | Muestra sitios web similares o relacionados al URL especificado.                                 | related:www.microsoft.com                                   |
| **info:**        | Muestra información sobre una página web específica.                                             | info:gothotel.com                                           |
| **location:**    | Devuelve resultados basados en una ubicación específica.                                         | location: 4 seasons restaurant                              |
| **filetype:**    | Busca archivos con una extensión específica.                                                     | jasmine filetype:jpg                                        |
| **source:**      | Muestra información de un sitio web específico en Google News.                                   | Malware news source:"Hacker News"                           |
| **phonebook:**   | Encuentra números telefónicos de personas u organizaciones.                                      | phonebook:Sundar Pichai                                     |
| **before:**      | Filtra resultados publicados antes de una fecha específica.                                      | ransomware before:2020-06-29                                |
| **after:**       | Filtra resultados publicados después de una fecha específica.                                    | site:wikipedia.org after:2023-01-01 artificial intelligence |
