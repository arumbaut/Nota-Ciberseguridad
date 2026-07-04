---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/941"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Post-explotación

---

Supongamos que explotamos con éxito el sistema objetivo durante el `Exploitation` escenario. Al igual que en la etapa de Explotación, debemos considerar nuevamente si utilizar o no `Evasive Testing` en el `Post-Exploitation` escenario. Ya estamos en el sistema en la fase post-explotación, lo que hace mucho más difícil evitar una alerta. El `Post-Exploitation` La etapa tiene como objetivo obtener información sensible y relevante para la seguridad desde una perspectiva local e información relevante para el negocio que, en la mayoría de los casos, requiere privilegios más altos que un usuario estándar. Esta etapa incluye los siguientes componentes:

|  |  |
| --- | --- |
| Pruebas evasivas | Recopilación de información |
| Saqueo | Evaluación de vulnerabilidades |
| Escalada de privilegios | Persistencia |
| Exfiltración de datos |  |

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-POEX.png)

---

## Pruebas evasivas

Si un administrador experto monitorea los sistemas, cualquier cambio o incluso un solo comando podría activar una alarma que nos delatará. En muchos casos, nos expulsan de la red y luego comienza la búsqueda de amenazas donde somos el foco. También podemos perder el acceso a un host (que se pone en cuarentena) o a una cuenta de usuario (que se desactiva temporalmente o se cambia la contraseña). Esta prueba de penetración habría fallado pero habría tenido éxito en algunos aspectos porque el cliente pudo detectar algunas acciones. Podemos brindar valor al cliente en esta situación al escribir una cadena de ataque completa y ayudarlo a identificar brechas en su monitoreo y procesos donde no notó nuestras acciones. Para nosotros, podemos estudiar cómo y por qué el cliente nos detectó y trabajar para mejorar nuestras habilidades de evasión. Quizás no probamos exhaustivamente una carga útil,o nos descuidamos y ejecutamos un comando como `net user` o `whoami` esto a menudo es monitoreado por sistemas EDR y marcado como actividad anómala.

> [!primary] Primary
> A menudo puede ayudar a nuestros clientes si ejecutamos comandos o herramientas que sus defensas detienen o detectan. Les muestra que sus defensas están trabajando en algunos ataques. Tenga en cuenta que estamos emulando a un atacante, por lo que no siempre es del todo malo que algunos de los ataques se hagan notar. Sin embargo, al realizar pruebas evasivas, nuestro objetivo debe ser pasar prácticamente desapercibido para que podamos identificar cualquier "punto ciego" que nuestros clientes tengan en sus entornos de red.

Las pruebas evasivas se dividen en tres categorías diferentes:

| **`Evasive`** | **`Hybrid Evasive`** | **`Non-Evasive`** |
| --- | --- | --- |

Esto no significa que no podamos utilizar los tres métodos. Supongamos que nuestro cliente desea realizar una prueba de penetración intrusiva para obtener la mayor cantidad de información posible y los resultados de pruebas más profundos. En ese caso, realizaremos `Non-Evasive` Pruebas, ya que las medidas de seguridad en la red pueden limitarnos e incluso detenernos. Sin embargo, esto también se puede combinar con `Evasive` pruebas, utilizando los mismos comandos y métodos para pruebas no evasivas. Podemos entonces ver si las medidas de seguridad pueden identificar y responder a las acciones realizadas. En `Hybrid-Evasive` Al realizar pruebas, podemos probar componentes específicos y medidas de seguridad que se han definido de antemano. Esto es común cuando el cliente solo quiere probar departamentos o servidores específicos para ver si pueden resistir los ataques.

---

## Recopilación de información

Dado que hemos adquirido una nueva perspectiva sobre el sistema y la red de nuestro sistema objetivo en la etapa de Explotación, estamos básicamente en un nuevo entorno. Esto significa que primero tenemos que volver a familiarizarnos con lo que estamos trabajando y qué opciones están disponibles. Por lo tanto, en el `Post-Exploitation` etapa, pasamos por la `Information Gathering` y `Vulnerability Assessment` etapas nuevamente, que podemos considerar como partes de la etapa actual. Esto se debe a que la información que teníamos hasta este momento fue recopilada desde una perspectiva externa, no interna.

Desde la perspectiva interna (local), tenemos muchas más posibilidades y alternativas para acceder a cierta información que es relevante para nosotros. Por tanto, la etapa de recopilación de información comienza de nuevo desde la perspectiva local. Buscamos y recopilamos tanta información como podemos. La diferencia aquí es que también enumeramos la red local y los servicios locales como impresoras, servidores de bases de datos, servicios de virtualización, etc. A menudo encontraremos recursos compartidos destinados a que los empleados los utilicen para intercambiar y compartir datos y archivos. La investigación de estos servicios y componentes de la red se denomina `Pillaging`.

---

## Saqueo

El saqueo es la etapa en la que examinamos el papel del anfitrión en la red corporativa. Analizamos las configuraciones de red, incluyendo pero no limitándonos a:

|  |  |  |
| --- | --- | --- |
| Interfaces | Enrutamiento | DNS |
| ARP | Servicios | VPN |
| Subredes IP | Acciones | Tráfico de red |

`Understanding the role of the system` we are on también nos brinda una excelente comprensión de cómo se comunica con otros dispositivos de red y su propósito. A partir de esto, podemos averiguar, por ejemplo, qué subdominios alternativos existen, si tiene múltiples interfaces de red, si hay otros hosts con los que se comunica este sistema, si los administradores se conectan a otros hosts desde él y si potencialmente podemos reutilizar credenciales o robar una clave SSH para ampliar nuestro acceso o establecer persistencia, etc. Esto ayuda, sobre todo, a obtener una visión general de la estructura de la red.

Por ejemplo, podemos utilizar las políticas instaladas en este sistema para determinar qué utilizan otros hosts en la red. Porque los administradores a menudo utilizan esquemas particulares para proteger su red y evitar que los usuarios cambien algo en ella. Por ejemplo, supongamos que descubrimos que la política de contraseñas requiere sólo ocho caracteres pero ningún carácter especial. En ese caso, podemos concluir que tenemos una probabilidad relativamente alta de adivinar las contraseñas de otros usuarios en este y otros sistemas.

Durante la etapa de saqueo, también buscaremos datos confidenciales como contraseñas en recursos compartidos, máquinas locales, scripts, archivos de configuración, bóvedas de contraseñas, documentos (Excel, Word, archivos.txt, etc.) e incluso correo electrónico.

Nuestros principales objetivos con el saqueo son mostrar el impacto de una explotación exitosa y, si aún no hemos alcanzado el objetivo de la evaluación, encontrar datos adicionales como contraseñas que puedan ser entradas para otras etapas como el movimiento lateral.

---

## Persistencia

Una vez que tenemos una descripción general del sistema, nuestro siguiente paso inmediato es mantener el acceso al host explotado. De esta forma, si se interrumpe la conexión, aún podremos acceder a ella. Este paso es esencial y a menudo se utiliza como el primer paso antes del `Information Gathering` y `Pillaging` Etapas.

Debemos seguir secuencias no estandarizadas porque cada sistema está configurado individualmente por un administrador único que aporta sus propias preferencias y conocimientos. Se recomienda que lo hagamos `work flexibly` durante esta fase `and adapt` a las circunstancias. Por ejemplo, supongamos que hemos utilizado un ataque de desbordamiento de búfer en un servicio que probablemente lo bloquee. En ese caso, debemos establecer persistencia en el sistema lo antes posible para evitar tener que atacar el servicio varias veces y potencialmente causar una interrupción. A menudo, si perdemos la conexión, no podremos acceder al sistema de la misma manera.

---

## Evaluación de vulnerabilidades

Si podemos mantener el acceso y tener una buena visión general del sistema, podemos utilizar la información sobre el sistema y sus servicios y cualquier otro dato almacenado en él para repetirlo `Vulnerability Assessment` etapa, pero esta vez desde dentro del sistema. Analizamos la información y la priorizamos en consecuencia. El objetivo que perseguimos a continuación es la escalada de privilegios (si aún no está en vigor).

Nuevamente, es esencial distinguir entre exploits que pueden dañar el sistema y ataques contra los servicios que no causan ninguna interrupción. Al hacerlo, sopesamos los componentes por los que ya hemos pasado en la primera etapa de Evaluación de Vulnerabilidad.

---

## Escalada de privilegios

La escalada de privilegios es significativa y, en la mayoría de los casos, representa un momento crítico que puede abrirnos muchas más puertas nuevas. Obtener los privilegios más altos posibles en el sistema o dominio suele ser crucial. Por eso queremos obtener los privilegios del `root` (en `Linux-based` sistemas) o el dominio `administrator` / `local administrator` / `SYSTEM` (en `Windows-based` sistemas) porque esto a menudo nos permitirá movernos por toda la red sin ninguna restricción.

Sin embargo, es esencial recordar que la escalada de privilegios no siempre tiene que ocurrir localmente en el sistema. También podemos obtener credenciales almacenadas durante la etapa de recopilación de información de otros usuarios que sean miembros de un grupo con mayores privilegios. Explotar estos privilegios para iniciar sesión como otro usuario también es parte de la escalada de privilegios porque hemos aumentado nuestros privilegios (rápidamente) utilizando el nuevo conjunto de credenciales.

---

## Exfiltración de datos

Durante el `Information Gathering` y `Pillaging` En esta etapa, a menudo podremos encontrar, entre otras cosas, información personal considerable y datos de clientes. Algunos clientes querrán comprobar si es posible exfiltrar este tipo de datos. Esto significa que intentamos transferir esta información del sistema de destino al nuestro. Sistemas de seguridad como `Data Loss Prevention` (`DLP`) și `Endpoint Detection and Response` (`EDR`) ayudar a detectar y prevenir la exfiltración de datos. Además de `Network Monitoring` Muchas empresas utilizan cifrado en los discos duros para evitar que terceros vean dicha información. Antes de exfiltrar cualquier dato real, debemos consultar con el cliente y nuestro gerente. A menudo puede ser suficiente crear algunos datos falsos (como números de tarjetas de crédito o números de seguro social falsos) y filtrarlos a nuestro sistema. De esa manera, se probarán los mecanismos de protección que buscan patrones en los datos que salen de la red, pero no seremos responsables de ningún dato confidencial en vivo en nuestra máquina de prueba.

Las empresas deben cumplir con las normas de seguridad de datos dependiendo del tipo de datos involucrados. Estos incluyen, entre otros:

| **Tipo de información** | **Reglamento de seguridad** |
| --- | --- |
| Información de la cuenta de tarjeta de crédito | `Payment Card Industry` (`PCI`) |
| Información electrónica sobre la salud del paciente | `Health Insurance Portability and Accountability Act` (`HIPAA`) |
| Información sobre banca privada para consumidores | `Gramm-Leach-Bliley` (`GLBA`) |
| Información gubernamental | `Federal Information Security Management Act of 2002` (`FISMA`) |

Algunos marcos que las empresas pueden seguir incluyen:

|  |  |
| --- | --- |
| (`NIST`) - Instituto Nacional de Estándares y Tecnología | (`CIS Controls`) - Centro de Controles de Seguridad de Internet |
| (`ISO`) - Organización Internacional de Normalización | (`PCI-DSS`) - El estándar de seguridad de datos de la industria de tarjetas de pago |
| (`GDPR`) - Reglamento General de Protección de Datos | (`COBIT`) - Objetivos de Control de la Información y Tecnologías Relacionadas |
| (`FedRAMP`) - El Programa Federal de Gestión de Riesgos y Autorizaciones | (`ITAR`) - Reglamento sobre el tráfico internacional de armas |
| (`AICPA`) - Instituto Americano de Contadores Públicos Certificado | (`NERC CIP Standards`) - Normas de protección de infraestructura crítica NERC |

Vale la pena familiarizarnos con cada uno de estos marcos, pero lo crucial para nosotros, sin embargo, es cómo manejamos esta información. Para nosotros, el tipo de datos no tiene mucha importancia, pero los controles necesarios a su alrededor sí, y como dijimos anteriormente, podemos simular la exfiltración de datos de la red como prueba de concepto de que es posible. Debemos consultar con el cliente para asegurarnos de que sus sistemas estén destinados a detectar el tipo de datos falsos que intentamos exfiltrar si tenemos éxito, para no tergiversar nada en nuestro informe.

Es un buen hábito realizar una grabación de pantalla (junto con tomar capturas de pantalla) como evidencia adicional de pasos tan vitales. Si solo tenemos acceso al terminal, podemos mostrar el nombre de host, la dirección IP, el nombre de usuario y la ruta correspondiente al archivo del cliente y tomar una captura de pantalla. Esto nos ayuda a demostrar de dónde se originaron los datos y que podríamos eliminarlos del entorno con éxito.

Si se encuentran datos confidenciales como este, nuestro cliente, por supuesto, debe ser informado inmediatamente. Teniendo en cuenta que podríamos aumentar los privilegios y exfiltrar datos personales, es posible que quieran pausar, finalizar o cambiar el enfoque de la prueba de penetración, especialmente si la exfiltración de datos fuera el objetivo principal. Sin embargo, esto queda a discreción de nuestro cliente y muchos preferirán que sigamos realizando pruebas para identificar todas las posibles debilidades en su entorno.

A continuación, analizaremos el movimiento lateral, una etapa clave en el proceso de pruebas de penetración que puede utilizar datos de nuestra posexplotación como entrada.