---
title: "Penetration Testing Process | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/936"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Pre-compromiso

---

El preenganche es la etapa de preparación para la prueba de penetración real. Durante esta etapa se formulan muchas preguntas y se realizan algunos acuerdos contractuales. El cliente nos informa sobre lo que quiere que se pruebe y le explicamos detalladamente cómo hacer que la prueba sea lo más eficiente posible.

También es esencial distinguir entre `deterministic` y `stochastic` procesos. Un proceso determinista es un proceso en el que cada estado depende causalmente de otros estados y eventos anteriores y está determinado por ellos. Un proceso estocástico es aquel en el que un estado se deriva de otros estados sólo con una cierta probabilidad. Aquí sólo se pueden suponer condiciones estadísticas. Para nosotros, varias de las definiciones anteriores se superponen. Utilizamos la definición del proceso de pruebas de penetración de las ciencias sociales para representar `a course of events connected` con `deterministic processes`. Esto se debe a que todos nuestros pasos se basan en los eventos y resultados que podemos descubrir o provocar.

Todo el proceso previo al compromiso consta de tres componentes esenciales:`A penetration testing process is defined by successive steps and events performed by the penetration tester to find a path to the predefined objective.`

Los procesos describen una secuencia específica de operaciones dentro de un período de tiempo particular que conduce al resultado deseado. También es fundamental tener en cuenta que los procesos no representan una receta fija y no son una guía paso a paso. Por lo tanto, nuestros procesos de pruebas de penetración deben ser gruesos y flexibles. Después de todo, cada cliente tiene una infraestructura, deseos y expectativas únicos.

---

## Etapas de prueba de penetración

También se pueden hacer excepciones en casos urgentes, cuando nos lanzamos a la reunión inicial, que también puede tener lugar a través de una conferencia en línea. Es fundamental saberlo `stages` para contratarnos para una prueba de penetración. Porque no podemos aceptar una orden así de todos. Imaginemos, por ejemplo, que un empleado de una empresa nos contrata con el pretexto de comprobar la seguridad de la red corporativa. Sin embargo, después de que terminamos la evaluación, resultó que este empleado quería dañar a su propia empresa y no tenía autorización para que la empresa se hiciera la prueba. Esto nos pondría en una situación crítica desde el punto de vista jurídico.

A continuación se muestra una lista de muestra (no exhaustiva) de miembros de la empresa que pueden estar autorizados a contratarnos para pruebas de penetración. Esto puede variar de una empresa a otra: las organizaciones más grandes no involucran directamente al personal de nivel C y la responsabilidad recae en la alta gerencia de TI, Auditoría o Seguridad de TI o similares.`stages` que permiten variar y adaptar de forma flexible los pasos y enfoques individuales a los resultados y la información que recibimos. Podemos desarrollar nuestro propio manual para varias cosas que probamos en diferentes etapas de una prueba de penetración, pero cada entorno es diferente y, por lo tanto, debemos adaptarnos constantemente.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process.png)

Es vital determinar desde el principio del proceso quién tiene la autoridad de signatario del contrato, los documentos de las Reglas de Compromiso y quiénes serán los puntos de contacto primarios y secundarios, el soporte técnico y el contacto para escalar cualquier problema.`optional study plan` sobre cómo proceder para aprender las numerosas Tácticas, Técnicas y Procedimientos (TTP), utilizando una estructura para mostrar cómo cada etapa se basa en la otra y también puede ser de naturaleza iterativa. Primero, veamos los componentes generales del proceso de pruebas de penetración y analicemos los módulos individuales y por qué son tan importantes.

Esta etapa también requiere la preparación de varios documentos antes de poder realizar una prueba de penetración que deben estar firmados por nuestro cliente y por nosotros para que la declaración de consentimiento también pueda presentarse por escrito si es necesario. De lo contrario, la prueba de penetración podría romper el `Information Gathering`. Estos documentos incluyen, entre otros:

| **Documento** | **Momento de la creación** |
| --- | --- |
| `1. Non-Disclosure Agreement` (`NDA`) | `After` Contacto inicial |
| `2. Scoping Questionnaire` | `Before` La reunión previa al compromiso |
| `3. Scoping Document` | `During` La reunión previa al compromiso |
| `4. Penetration Testing Proposal` (`Contract/Scope of Work` (`SoW`)) | `During` La reunión previa al compromiso |
| `5. Rules of Engagement` (`RoE`) | `Before` La reunión de inicio |
| `6. Contractors Agreement` (Evaluaciones físicas) | `Before` La reunión de inicio |
| `7. Reports` | `During` y `after` la prueba de penetración realizada |

Nota: Nuestro cliente puede proporcionar un documento de alcance separado que enumere las direcciones IP/rangos/URL dentro del alcance y cualquier credencial necesaria, pero esta información también debe documentarse como un apéndice en el documento RoE.

**Nota importante:**

Estos documentos deben ser revisados y adaptados por un abogado una vez preparados.

---

## Cuestionario de alcance

Una vez realizado el contacto inicial con el cliente, normalmente le enviamos un `Scoping Questionnaire` para comprender mejor los servicios que buscan. Este cuestionario de alcance debe explicar claramente nuestros servicios y normalmente puede pedirles que elijan uno o más de la siguiente lista:

|  |  |
| --- | --- |
| ☐ Evaluación de vulnerabilidad interna | ☐ Evaluare de vulnerabilitate externă |
| ☐ Prueba de penetración interna | ☐ Prueba de penetración externa |
| ☐ Evaluación de seguridad inalámbrica | ☐ Evaluación de seguridad de aplicaciones |
| ☐ Evaluación de seguridad física | ☐ Evaluación de Ingeniería Social |
| ☐ Evaluación del equipo rojo | ☐ Evaluación de seguridad de aplicaciones web |

En cada uno de ellos, el cuestionario debe permitir al cliente ser más específico sobre la evaluación requerida. ¿Necesitan una aplicación web o una evaluación de aplicaciones móviles? ¿Revisión segura del código? ¿La prueba de penetración interna debe ser de caja negra y semievasiva? ¿Quieren sólo una evaluación de phishing como parte de la Evaluación de Ingeniería Social o también llamadas de vishing? Esta es nuestra oportunidad de explicar la profundidad y amplitud de nuestros servicios, asegurarnos de comprender las necesidades y expectativas de nuestros clientes y asegurarnos de que podemos brindarles adecuadamente la evaluación que requieren.

Además del tipo de evaluación, el nombre del cliente, la dirección y la información de contacto clave del personal, otros datos críticos incluyen:

|  |  |
| --- | --- |
| ¿Cuántos anfitriones en vivo se esperaban? |  |
| ¿Cuántos rangos de IP/CIDR tiene alcance? |  |
| ¿Cuántos dominios/subdominios están dentro del alcance? |  |
| ¿Cuántos SSID inalámbricos hay en el alcance? |  |
| ¿Cuántas aplicaciones web/móviles? Si las pruebas están autenticadas, ¿cuántos roles (usuario estándar, administrador, etc.)? |  |
| Para una evaluación de phishing, ¿cuántos usuarios serán el objetivo? ¿El cliente proporcionará una lista o se nos pedirá que la recopilemos a través de OSINT? |  |
| Si el cliente solicita una Evaluación Física, ¿cuántas ubicaciones? Si hay varios sitios dentro del alcance, ¿están dispersos geográficamente? |  |
| ¿Cuál es el objetivo de la Evaluación del Equipo Rojo? ¿Hay alguna actividad (como phishing o ataques de seguridad física) fuera de alcance? |  |
| ¿Se desea una evaluación de seguridad de Active Directory separada? |  |
| ¿Las pruebas de red se realizarán desde un usuario anónimo en la red o desde un usuario de dominio estándar? |  |
| ¿Necesitamos eludir el control de acceso a la red (NAC)? |  |

Por último, nos gustaría preguntar sobre la divulgación de información y la evasión (si corresponde al tipo de evaluación):

- Es la caja negra de la prueba de penetración (no se proporciona información), la caja gris (solo se proporcionan direcciones IP/rangos CIDR/URL) y la caja blanca (se proporciona información detallada)
- ¿les gustaría que probáramos desde un no evasivo, híbrido-evasivo (comience en silencio y gradualmente se vuelva "más fuerte" para evaluar en qué nivel el personal de seguridad del cliente detecta nuestras actividades) o totalmente evasivo.

Esta información nos ayudará a garantizar que asignamos los recursos adecuados y entregamos el compromiso en función de las expectativas del cliente. Esta información también es necesaria para proporcionar una propuesta precisa con un cronograma del proyecto (por ejemplo, una evaluación de vulnerabilidad tomará considerablemente menos tiempo que una evaluación de equipo rojo) y un costo (una prueba de penetración externa contra 10 IP costará significativamente menos que una prueba de penetración interna con 30/24 redes dentro del alcance).

Con base en la información que recibimos del cuestionario de alcance, creamos una descripción general y resumimos toda la información en el `Scoping Document`.

---

## Reunión previa al compromiso

Una vez que tengamos una idea inicial de los requisitos del proyecto del cliente, podemos pasar a la `pre-engagement meeting`. En esta reunión se discuten todos los componentes relevantes y esenciales con el cliente antes de la prueba de penetración, explicándolos a nuestro cliente. La información que recopilemos durante esta fase, junto con los datos recopilados del cuestionario de alcance, servirán como insumos para la `Penetration Testing Proposal`, también conocido como el `Contract` o `Scope of Work` (`SoW`). Podemos pensar en todo el proceso como una visita al médico para informarnos sobre los exámenes previstos. Esta fase generalmente ocurre por correo electrónico y durante una conferencia telefónica en línea o una reunión en persona.

Nota: Es posible que durante nuestra carrera nos encontremos con clientes que se estén sometiendo a su primera prueba de penetración, o que el cliente directo PoC no esté familiarizado con el proceso. No es raro utilizar parte de la reunión previa al compromiso para revisar el cuestionario de alcance, ya sea en parte o paso a paso.

#### Contrato - Lista de verificación

| **Punto de control** | **Descripción** |
| --- | --- |
| `☐ NDA` | El Acuerdo de confidencialidad (NDA) se refiere a un contrato de secreto entre el cliente y el contratista con respecto a toda la información escrita o verbal relativa a un pedido/proyecto. El contratista se compromete a tratar toda la información confidencial que se le comunique como estrictamente confidencial, incluso después de que se complete el pedido/proyecto. Además, en el acuerdo se estipularán las excepciones a la confidencialidad, la transferibilidad de derechos y obligaciones y las sanciones contractuales. La NDA debe firmarse antes de la reunión inicial o, a más tardar, durante la reunión, antes de discutir cualquier información en detalle. |
| `☐ Goals` | Los objetivos son hitos que deben alcanzarse durante el pedido/proyecto. En este proceso, el establecimiento de objetivos se inicia con los objetivos importantes y continúa con los más detallados y pequeños. |
| `☐ Scope` | Se discuten y definen los componentes individuales que se van a probar. Estos pueden incluir dominios, rangos de IP, hosts individuales, cuentas específicas, sistemas de seguridad, etc. Nuestros clientes pueden esperar que descubramos uno u otro punto por nosotros mismos. Sin embargo, la base legal para probar los componentes individuales tiene aquí la máxima prioridad. |
| `☐ Penetration Testing Type` | A la hora de elegir el tipo de prueba de penetración, presentamos las opciones individuales y explicamos las ventajas y desventajas. Dado que ya conocemos los objetivos y el alcance de nuestros clientes, también podemos y debemos hacer una recomendación sobre lo que aconsejamos y justificar nuestra recomendación en consecuencia. Qué tipo se utiliza al final es decisión del cliente. |
| `☐ Methodologies` | Ejemplos: OSSTMM, OWASP, análisis automatizado y manual no autenticado de los componentes de red internos y externos, evaluaciones de vulnerabilidad de componentes de red y aplicaciones web, vectorización, verificación y explotación de amenazas de vulnerabilidad, y desarrollo de exploits para facilitar técnicas de evasión. |
| `☐ Penetration Testing Locations` | Externo: Remoto (a través de VPN segura) y/o Interno: Interno o Remoto (a través de VPN segura) |
| `☐ Time Estimation` | Para la estimación del tiempo necesitamos las fechas de inicio y finalización de la prueba de penetración. Esto proporciona una ventana de tiempo precisa para realizar la prueba y nos ayuda a planificar nuestro procedimiento. También es vital determinar explícitamente la duración de las ventanas de tiempo para cada fase del ataque, como Explotación, Post-Explotación y Movimiento Lateral. Estos pueden realizarse durante o fuera del horario laboral habitual. Al realizar pruebas fuera del horario laboral habitual, la atención se centra más en las soluciones y sistemas de seguridad que deberían resistir nuestros ataques. |
| `☐ Third Parties` | Para los terceros, se debe determinar a través de qué proveedores externos nuestro cliente obtiene servicios. Estos pueden ser proveedores de nube, ISP y otros proveedores de alojamiento. Nuestro cliente debe obtener el consentimiento por escrito de estos proveedores describiendo que están de acuerdo y son conscientes de que ciertas partes de su servicio estarán sujetas a un ataque de piratería simulado. También es muy recomendable exigir al contratista que envíe el permiso de terceros que nos envió para que tengamos confirmación real de que efectivamente se ha obtenido dicho permiso. |
| `☐ Evasive Testing` | Las pruebas evasivas son la prueba de evadir y pasar el tráfico de seguridad y los sistemas de seguridad en la infraestructura del cliente. Buscamos técnicas que nos permitan conocer información sobre los componentes internos y atacarlos. Depende de si nuestro contratista quiere que utilicemos dichas técnicas o no. |
| `☐ Risks` | También debemos informar a nuestro cliente sobre los riesgos que implican las pruebas y las posibles consecuencias. En función de los riesgos y su posible gravedad, podemos establecer las limitaciones y tomar ciertas precauciones. |
| `☐ Scope Limitations & Restrictions` | También es fundamental determinar qué servidores, estaciones de trabajo u otros componentes de red son esenciales para el correcto funcionamiento del cliente y sus clientes. Tendremos que evitarlos y no debemos influir más en ellos, ya que esto podría dar lugar a errores técnicos críticos que también podrían afectar a los clientes de nuestros clientes en producción. |
| `☐ Information Handling` | HIPAA, PCI, HITRUST, FISMA/NIST, etc. |
| `☐ Contact Information` | Para obtener la información de contacto, necesitamos crear una lista del nombre, título, puesto de trabajo, dirección de correo electrónico, número de teléfono, número de teléfono de la oficina y una orden de prioridad de escalada de cada persona. |
| `☐ Lines of Communication` | También debe documentarse qué canales de comunicación se utilizan para intercambiar información entre el cliente y nosotros. Esto puede implicar correspondencia por correo electrónico, llamadas telefónicas o reuniones personales. |
| `☐ Reporting` | Además de la estructura del informe, también se analizan los requisitos específicos del cliente que debe contener el informe. Además, aclaramos cómo se realizará la presentación de informes y si se desea una presentación de los resultados. |
| `☐ Payment Terms` | Finalmente se explican los precios y las condiciones de pago. |

El elemento más crucial de esta reunión es la presentación detallada de la prueba de penetración a nuestro cliente y su enfoque. Como ya sabemos, cada pieza de infraestructura es única en su mayor parte y cada cliente tiene preferencias particulares a las que concede mayor importancia. Descubrir estas prioridades es una parte esencial de esta reunión.

Podemos pensar en ello como si hiciéramos un pedido en un restaurante. Si queremos un bistec medio crudo y el chef nos regala un bistec bien hecho porque cree que es mejor, no será lo que esperábamos. Por lo tanto, debemos priorizar los deseos de nuestros clientes y servir el filete tal como lo pidieron.

Basado en el `Contract Checklist` y la información de entrada compartida en el alcance, el `Penetration Testing Proposal` (`Contract`) y los asociados `Rules of Engagement` (`RoE`) se crean.

#### Reglas de compromiso - Lista de verificación

| **Punto de control** | **Contenido** |
| --- | --- |
| `☐ Introduction` | Descripción de este documento. |
| `☐ Contractor` | Nombre de la empresa, nombre completo del contratista, puesto de trabajo. |
| `☐ Penetration Testers` | Nombre de la empresa, nombre completo de pentesters. |
| `☐ Contact Information` | Direcciones de correo, direcciones de correo electrónico y números de teléfono de todas las partes clientes y evaluadores de penetración. |
| `☐ Purpose` | Descripción del propósito de la prueba de penetración realizada. |
| `☐ Goals` | Descripción de los objetivos que se deben alcanzar con la prueba de penetración. |
| `☐ Scope` | Todas las IP, nombres de dominio, URL o rangos CIDR. |
| `☐ Lines of Communication` | Conferencias en línea o llamadas telefónicas o reuniones cara a cara, o por correo electrónico. |
| `☐ Time Estimation` | Fechas de inicio y finalización. |
| `☐ Time of the Day to Test` | Horarios del día para realizar pruebas. |
| `☐ Penetration Testing Type` | Prueba de penetración externa/interna/Evaluaciones de vulnerabilidad/Ingeniería social. |
| `☐ Penetration Testing Locations` | Descripción de cómo se establece la conexión a la red cliente. |
| `☐ Methodologies` | OSSTMM, PTES, OWASP y otros. |
| `☐ Objectives / Flags` | Usuarios, archivos específicos, información específica y otros. |
| `☐ Evidence Handling` | Cifrado, protocolos seguros |
| `☐ System Backups` | Archivos de configuración, bases de datos y otros. |
| `☐ Information Handling` | Fuerte cifrado de datos |
| `☐ Incident Handling and Reporting` | Casos de contacto, interrupciones pentest, tipo de informes |
| `☐ Status Meetings` | Frecuencia de reuniones, fechas, horarios, fiestas incluidas |
| `☐ Reporting` | Tipo, lectores objetivo, enfoque |
| `☐ Retesting` | Fechas de inicio y finalización |
| `☐ Disclaimers and Limitation of Liability` | Daños en el sistema, pérdida de datos |
| `☐ Permission to Test` | Contrato firmado, acuerdo de contratistas |

---

## Reunión de inicio

El `kick-off meeting` Generalmente ocurre a una hora programada y en persona después de firmar todos los documentos contractuales. Esta reunión generalmente incluye POC(s) del cliente (de Auditoría Interna, Seguridad de la Información, TI, Gobernanza y Riesgo, etc., según el cliente), personal de soporte técnico del cliente (desarrolladores, administradores de sistemas, ingenieros de redes, etc.) y el equipo de pruebas de penetración (alguien en un rol de gestión (como el líder de práctica), el probador(es) de penetración real, y en ocasiones un Gerente de Proyecto o incluso el Ejecutivo de Cuentas de Ventas o similar). Repasaremos la naturaleza de la prueba de penetración y cómo se llevará a cabo. Por lo general, no hay pruebas de denegación de servicio (DoS). También explicamos que si se identifica una vulnerabilidad crítica, se pausarán las actividades de pruebas de penetración y se generará un informe de notificación de vulnerabilidady se contactará a los contactos de emergencia. Normalmente, estos solo se generan durante pruebas de penetración externa para detectar fallas críticas, como ejecución remota de código (RCE) no autenticada, inyección SQL u otra falla que conduzca a la divulgación de datos confidenciales. El propósito de esta notificación es permitir al cliente evaluar el riesgo internamente y determinar si el problema justifica una solución de emergencia. Por lo general, solo detendríamos una prueba de penetración interna y alertaríamos al cliente si un sistema deja de responder, encontramos evidencia de actividad ilegal (como contenido ilegal en un archivo compartido) o la presencia de un actor de amenaza externo en la red o una violación previa.u otra falla que conduzca a la divulgación de datos confidenciales. El propósito de esta notificación es permitir al cliente evaluar el riesgo internamente y determinar si el problema justifica una solución de emergencia. Por lo general, solo detendríamos una prueba de penetración interna y alertaríamos al cliente si un sistema deja de responder, encontramos evidencia de actividad ilegal (como contenido ilegal en un archivo compartido) o la presencia de un actor de amenaza externo en la red o una violación previa.u otra falla que conduzca a la divulgación de datos confidenciales. El propósito de esta notificación es permitir al cliente evaluar el riesgo internamente y determinar si el problema justifica una solución de emergencia. Por lo general, solo detendríamos una prueba de penetración interna y alertaríamos al cliente si un sistema deja de responder, encontramos evidencia de actividad ilegal (como contenido ilegal en un archivo compartido) o la presencia de un actor de amenaza externo en la red o una violación previa.Encontramos evidencia de actividad ilegal (como contenido ilegal en un archivo compartido) o la presencia de un actor de amenaza externo en la red o una violación previa.Encontramos evidencia de actividad ilegal (como contenido ilegal en un archivo compartido) o la presencia de un actor de amenaza externo en la red o una violación previa.

También debemos informar a nuestros clientes sobre los riesgos potenciales durante una prueba de penetración. Por ejemplo, debemos mencionar que una prueba de penetración puede dejar muchos `log entries and alarms` en sus aplicaciones de seguridad. Además, si se utiliza fuerza bruta o cualquier ataque similar, también vale la pena mencionar que podemos hacerlo accidentalmente `lock some users` encontrado durante la prueba de penetración. También debemos informar a nuestros clientes que deben contactarnos inmediatamente si se realiza la prueba de penetración `negatively impacts their network`.

Explicar el proceso de prueba de penetración brinda a todos los involucrados una idea clara de todo nuestro proceso. Esto demuestra nuestro enfoque profesional y convence a quienes nos preguntan de que sabemos lo que estamos haciendo. Porque aparte del personal técnico, el CTO y el CISO, sonará como un cierto tipo de magia que es muy difícil de entender para los profesionales no técnicos. Por lo tanto, debemos ser conscientes de nuestra audiencia y dirigirnos al interrogador técnicamente más inexperto para que todos con quienes hablamos puedan seguir nuestro enfoque.

Es necesario discutir y aclarar todos los puntos relacionados con las pruebas. Es fundamental responder con precisión a los deseos y expectativas del cliente. Cada estructura y red empresarial es diferente y requiere un enfoque adaptado. Cada cliente tiene objetivos diferentes y debemos ajustar nuestras pruebas a sus deseos. Por lo general, podemos ver cuán experimentados tienen nuestros clientes al someterse a pruebas de penetración al principio de la llamada, por lo que es posible que tengamos que cambiar nuestro enfoque para explicar las cosas con más detalle y estar preparados para responder más preguntas, o la llamada inicial puede ser muy rápida y sencilla.

---

## Acuerdo de contratistas

Si la prueba de penetración también incluye pruebas físicas, entonces se requiere un acuerdo adicional del contratista. Dado que no se trata sólo de un entorno virtual sino también de una intrusión física, aquí se aplican leyes completamente diferentes. También es posible que muchos de los empleados no hayan sido informados sobre la prueba. Supongamos que nos encontramos con empleados con una conciencia de seguridad muy alta durante el ataque físico y los intentos de ingeniería social, y nos atrapan. En ese caso, los empleados, en la mayoría de los casos, se pondrán en contacto con la policía. Este adicional `contractor's agreement` es nuestro " `get out of jail free card` " en este caso.

#### Acuerdo de contratistas: lista de verificación para evaluaciones físicas

| **Punto de control** |
| --- |
| `☐ Introduction` |
| `☐ Contractor` |
| `☐ Purpose` |
| `☐ Goal` |
| `☐ Penetration Testers` |
| `☐ Contact Information` |
| `☐ Physical Addresses` |
| `☐ Building Name` |
| `☐ Floors` |
| `☐ Physical Room Identifications` |
| `☐ Physical Components` |
| `☐ Timeline` |
| `☐ Notarization` |
| `☐ Permission to Test` |

---

## Configuración

Una vez resueltos todos los puntos anteriores y disponemos de la información necesaria, planificamos nuestro enfoque y preparamos todo. Descubriremos que aún se desconocen los resultados de las pruebas de penetración, pero podemos preparar nuestras máquinas virtuales, VPS y otras herramientas/sistemas para todos los escenarios y situaciones. Puede encontrar más información y cómo preparar estos sistemas en el [Configuración](https://academy.hackthebox.com/module/details/87) módulo.