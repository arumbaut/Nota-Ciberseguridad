---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/727"
author:
published:
created: 2026-06-08
description:
tags:
  - "clippings"
---
## Empezando

---

Como principiante en seguridad de la información, puede resultar extremadamente desalentador saber por dónde empezar. Hemos visto a personas de todos los ámbitos de la vida comenzar con poco o ningún conocimiento y tener éxito en la plataforma HTB y, en consecuencia, comenzar el viaje por una carrera técnica. Existen muchos recursos excelentes para principiantes, que incluyen capacitación gratuita y paga, máquinas y laboratorios deliberadamente vulnerables, sitios web de tutoriales, blogs, canales de YouTube, etc.

A lo largo de nuestro viaje, veremos continuamente los términos `guided` y `exploratory` aprendiendo.

La Academia HTB sigue un `guided` Enfoque de aprendizaje donde los estudiantes trabajan a través de un módulo sobre un tema determinado, leyendo el material y reproduciendo los ejemplos para reforzar los temas presentados. La mayoría de las secciones del módulo tienen uno o más ejercicios prácticos para poner a prueba el conocimiento de los estudiantes sobre un tema determinado. Muchos módulos culminan en una evaluación de habilidades de varios pasos para probar la comprensión de los estudiantes del material presentado en las secciones del módulo cuando se aplica a un escenario del mundo real.

El aprendizaje guiado tiene el beneficio de proporcionar a los estudiantes métodos estructurados para aprender diversas técnicas de una manera que desarrolle correctamente sus conocimientos, además de proporcionar material adicional, conocimientos previos y vínculos con el mundo real para aprender sobre un tema en profundidad y al mismo tiempo obligarlos a probar sus conocimientos en varios puntos de control a lo largo del proceso de aprendizaje.

La plataforma HTB principal sigue un `exploratory` enfoque de aprendizaje para colocar a los usuarios en una amplia variedad de escenarios del mundo real en los que tienen que utilizar sus habilidades y procesos técnicos, como la enumeración, para lograr un objetivo, a menudo desconocido. La plataforma ofrece desafíos únicos en categorías como ingeniería inversa, criptografía, esteganografía, pwn, web, ciencia forense, OSINT, dispositivos móviles, hardware y más en varios niveles de dificultad diseñados para probar habilidades técnicas y de pensamiento crítico.

También hay máquinas individuales (cajas) de varios tipos de sistemas operativos, minilaboratorios pequeños (y desafiantes) llamados Endgames, Fortresses, que son máquinas individuales que contienen muchos desafíos, y Pro Labs, que son grandes redes empresariales simuladas donde los usuarios pueden realizar una prueba de penetración simulada en varios niveles de dificultad.

Siempre hay máquinas "activas" gratuitas y desafíos que los usuarios deben atacar desde un enfoque de "caja negra" o con poco o ningún conocimiento previo de la tarea en cuestión. Las máquinas, los desafíos y los finales se "retiran" y están disponibles para usuarios VIP junto con tutoriales oficiales para ayudar en el proceso de aprendizaje. Cuando se retira contenido de la plataforma, la comunidad puede crear blogs y tutoriales en vídeo. Vale la pena leer varios blogs/ver varios videos en la misma máquina retirada para ver las diferentes perspectivas y estilos que adoptan los usuarios al abordar una tarea para comenzar a construir el enfoque con el que se sientan más cómodos.

El `exploratory` El principal beneficio del enfoque de aprendizaje es permitirnos confiar en nuestras habilidades para ingresar a las máquinas y resolver desafíos, lo que nos ayuda a desarrollar nuestras metodologías y técnicas y nos ayuda a dar forma a nuestro estilo de pruebas de penetración.

**Siempre es bueno mezclar los dos estilos de aprendizaje para que construyamos nuestras habilidades con la estructura adecuada de conocimiento y nos desafiemos a profundizar nuestra comprensión de las habilidades que aprendimos.**

---

## Recursos

Al comenzar, la gran cantidad de contenido disponible en la web puede resultar abrumadora. Además, no es fácil saber por dónde empezar y la calidad de los materiales disponibles. Lo que sigue son algunos recursos fuera de HTB que recomendamos a cualquiera que comience su viaje o busque mejorar sus habilidades y aprender nuevos trucos.

#### Máquinas/aplicaciones vulnerables

Hay muchos recursos disponibles para practicar vulnerabilidades comunes de la web y la red en un entorno seguro y controlado. Los siguientes son algunos ejemplos de aplicaciones web deliberadamente vulnerables y máquinas vulnerables que podemos configurar en un entorno de laboratorio para practicar más.

|  |  |
| --- | --- |
| [Tienda de jugos OWASP](https://owasp.org/www-project-juice-shop/) | Es una aplicación web vulnerable moderna escrita en Node.js, Express y Angular que muestra todo [Los diez mejores de OWASP](https://owasp.org/www-project-top-ten) junto con muchas otras fallas de seguridad de aplicaciones del mundo real. |
| [Metasplotable 2](https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/) | Es una máquina virtual Ubuntu Linux deliberadamente vulnerable que se puede utilizar para practicar enumeración, explotación automatizada y manual. |
| [Metasplotable 3](https://github.com/rapid7/metasploitable3) | Es una plantilla para crear una máquina virtual Windows vulnerable configurada con una amplia gama de [vulnerabilidades](https://github.com/rapid7/metasploitable3/wiki/Vulnerabilities). |
| [DVWA](https://github.com/digininja/DVWA) | Esta es una aplicación web PHP/MySQL vulnerable que muestra muchas vulnerabilidades comunes de aplicaciones web con distintos grados de dificultad. |

Vale la pena aprender a configurarlos en su entorno de laboratorio para obtener práctica adicional en la configuración de máquinas virtuales y trabajar con configuraciones comunes, como configurar un servidor web. Además de estas máquinas/aplicaciones vulnerables, también podemos configurar muchas máquinas y aplicaciones en un entorno de laboratorio para practicar la configuración, enumeración/explotación y remediación.

---

#### Canales de YouTube

Hay muchos canales de YouTube que muestran pruebas de penetración y técnicas de piratería. Algunos que vale la pena marcar como favoritos son:

|  |  |
| --- | --- |
| [IppSec](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA) | Proporciona un recorrido extremadamente profundo por cada caja HTB retirada repleta de información de su propia experiencia, así como videos sobre diversas técnicas. |
| [VbScrub](https://www.youtube.com/channel/UCpoyhjwNIWZmsiKNKpsMAQQ) | Proporciona vídeos HTB, así como vídeos sobre técnicas, centrándose principalmente en la explotación de Active Directory. |
| [STÖK](https://www.youtube.com/channel/UCQN2DsjnYH60SFBIA6IkNwg) | Proporciona videos sobre diversos temas relacionados con la seguridad de la información, centrándose principalmente en recompensas por errores y pruebas de penetración de aplicaciones web. |
| [Desbordamiento en vivo](https://www.youtube.com/channel/UClcE-kVhqyiHCcjYwcpfj9w) | Proporciona vídeos sobre una amplia variedad de temas técnicos de seguridad de la información. |

---

#### Blogs

Hay demasiados blogs como para enumerarlos todos. Si realiza una búsqueda en Google de un tutorial de casi cualquier equipo HTB retirado, generalmente encontrará los mismos blogs una y otra vez. Estos pueden ser excelentes para ver la perspectiva de otra persona sobre el mismo tema, especialmente si sus publicaciones contienen información "extra" sobre el objetivo que otros blogs no cubren.  
Un gran blog que vale la pena visitar es [0xdf hackea cosas](https://0xdf.gitlab.io/). Este blog tiene tutoriales fantásticos de la mayoría de las cajas HTB retiradas, cada una con una sección "Más allá de la raíz" que cubre algún aspecto único de la caja que notó el autor. El blog también tiene publicaciones sobre diversas técnicas, análisis de malware y artículos de eventos CTF anteriores.

En cualquier momento del proceso de aprendizaje, vale la pena leer la mayor cantidad de material posible para comprender mejor un tema y obtener diferentes perspectivas. Además de los blogs relacionados con cajas HTB retiradas, también vale la pena buscar artículos de blogs sobre exploits/ataques recientes, técnicas de explotación de Active Directory, artículos sobre eventos CTF y artículos sobre informes de recompensas por errores. Todos ellos pueden contener una gran cantidad de información que puede ayudar a conectar algunos puntos en nuestro aprendizaje o incluso enseñarnos algo nuevo que pueda resultar útil en una evaluación.

---

#### Sitios web tutoriales

Existen muchos sitios web de tutoriales para practicar habilidades fundamentales de TI, como la creación de scripts.  
Dos excelentes sitios web de tutoriales son [Debajo del alambre](https://underthewire.tech/wargames) y [Sobre el cable](https://overthewire.org/wargames/). Estos sitios web están configurados para ayudar a capacitar a los usuarios en el uso de Windows `PowerShell` y la línea de comandos de Linux, respectivamente, a través de varios escenarios en formato de "juegos de guerra".  
Llevan al usuario a través de varios niveles, que consisten en tareas o desafíos para entrenarlo en el uso fundamental y avanzado de la línea de comandos de Windows y Linux `Bash` y `PowerShell` scripting. Estas habilidades son primordiales para cualquiera que busque tener éxito en esta industria.

---

#### Punto de partida del HTB

[Punto de partida](https://app.hackthebox.com/starting-point) es una introducción a los laboratorios HTB y a las máquinas/desafíos básicos. Después de completar un tutorial que cubre la conexión a VPN, la enumeración, cómo afianzarse y la escalada de privilegios contra un solo objetivo, se nos presentan varias máquinas fácilmente calificadas que pueden ser atacadas antes de acceder al resto de la plataforma HTB.

---

#### Pistas HTB

En la plataforma principal HTB [Pistas](https://app.hackthebox.com/tracks), "selecciones de máquinas y desafíos vinculados entre sí para que los usuarios progresen y dominen un tema en particular" Las pistas cubren una variedad de temas y se agregan continuamente a la plataforma. Su objetivo es ayudar a los estudiantes a mantenerse enfocados en un objetivo específico de manera estructurada mientras siguen un enfoque de aprendizaje exploratorio.

---

#### Máquinas HTB aptas para principiantes

Hay muchas máquinas aptas para principiantes en la plataforma HTB principal. Algunos recomendados son:

| [Cojo](https://app.hackthebox.com/machines/1) | [Azul](https://app.hackthebox.com/machines/51) | [Mordisquear](https://app.hackthebox.com/machines/121) | [Shocker](https://app.hackthebox.com/machines/108) | [Jerry](https://app.hackthebox.com/machines/144) |
| --- | --- | --- | --- | --- |

Si prefiere ver un tutorial en video mientras trabaja en una máquina Easy, las siguientes listas de reproducción del canal de IppSec tienen tutoriales para varios equipos HTB Easy de Linux/Windows:

| **  Cajas Linux fáciles  ** | **  Cajas sencillas para Windows  ** |
| --- | --- |

![](https://www.youtube.com/watch?v=videoseries)
![](https://www.youtube.com/watch?v=videoseries)

---

#### Desafíos de HTB aptos para principiantes

La plataforma HTB contiene desafíos únicos en una variedad de categorías. Algunos desafíos aptos para principiantes incluyen:

| [Encuentra el pase fácil](https://app.hackthebox.com/challenges/5) | [RSA débil](https://app.hackthebox.com/challenges/6) | [Conoces 0xDiablos](https://app.hackthebox.com/challenges/106) |
| --- | --- | --- |

---

#### Dante Prolab

La plataforma HTB tiene varios Pro Labs que son redes empresariales simuladas con muchos hosts interconectados que los jugadores pueden usar para practicar sus habilidades en una red que contiene múltiples objetivos.  
La explotación exitosa de hosts específicos proporcionará información que ayudará a los jugadores a la hora de atacar a los hosts que se encuentren más adelante en el laboratorio.

El [Laboratorio Dante Pro](https://app.hackthebox.com/prolabs/overview/dante) es el laboratorio más amigable para principiantes que se ofrece hasta la fecha. Este laboratorio está orientado a jugadores con cierta experiencia en la realización de ataques a redes y aplicaciones web y una comprensión de los conceptos de redes y los conceptos básicos de las metodologías de penetración, como escaneo/enumeración, movimiento lateral, escalada de privilegios, posexplotación, etc.

---

## Continuando

Ahora que hemos cubierto la terminología y las técnicas básicas y el escaneo/enumeración, juntemos las piezas recorriendo paso a paso un cuadro HTB de fácil calificación.