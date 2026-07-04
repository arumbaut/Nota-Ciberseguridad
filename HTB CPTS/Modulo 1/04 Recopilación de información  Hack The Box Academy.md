---
title: "Recopilación de información | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/938"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Recopilación de información

---

Una vez completada la fase previa al compromiso y todas las partes hayan firmado todos los términos y condiciones contractuales, `information gathering` comienza la fase. La recopilación de información es una parte esencial de cualquier evaluación de seguridad. Esta es la fase en la que recopilamos toda la información disponible sobre la empresa, sus empleados e infraestructura, y cómo están organizados. La recopilación de información es la fase más frecuente y vital a lo largo del proceso de pruebas de penetración, a la que volveremos una y otra vez.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-IG.png)

Todos los pasos que tomamos para explotar las vulnerabilidades se basan en la información que enumeramos sobre nuestros objetivos. Esta fase puede considerarse la piedra angular de cualquier ensayo de penetración. Podemos obtener la información necesaria que sea relevante para nosotros de muchas maneras diferentes. Sin embargo, podemos dividirlos en las siguientes categorías:

- An analysis is a detailed examination of an event or process, describing its origin and impact, that with the help of certain precautions and actions, can be triggered to support or prevent future occurrences.

Las cuatro categorías deben y tienen que ser realizadas por nosotros para cada prueba de penetración. Esto se debe a que `information` es el componente principal que nos lleva a realizar pruebas de penetración exitosas e identificar vulnerabilidades de seguridad. Podemos obtener esta información en cualquier lugar, ya sea en las redes sociales, en ofertas de trabajo, en hosts y servidores individuales o incluso en los empleados. La información se difunde y comparte continuamente en todas partes.

Después de todo, los humanos nos comunicamos intercambiando información, pero los componentes y servicios de la red se comunican de manera similar. Cualquier intercambio de información siempre tiene un propósito específico. En el caso de las redes informáticas, el objetivo es siempre desencadenar un proceso concreto. Ya sea almacenando datos en una base de datos, registrándolos, generando valores específicos o reenviando la información.


<div class="overflow-x-auto rounded-lg"><table class="bg-neutral-800 text-primary w-full"><thead class="text-left rounded-t-lg"><tr class="border-t-neutral-600 first:border-t-0 border-t"><th class="bg-neutral-700 first:rounded-tl-lg last:rounded-tr-lg p-4"><strong class="font-bold"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Tipo de análisis</font></font></strong></th><th class="bg-neutral-700 first:rounded-tl-lg last:rounded-tr-lg p-4"><strong class="font-bold"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Descripción</font></font></strong></th></tr></thead><tbody class="font-mono text-sm"><tr class="border-t-neutral-600 first:border-t-0 border-t"><td class="p-4"><code dir="ltr" class="bg-neutral-700 mb-6 text-blue-250 py-1 px-1.5">Descriptive</code></td><td class="p-4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">El análisis descriptivo es esencial en cualquier análisis de datos. Por un lado, describe un conjunto de datos basado en características individuales. Ayuda a detectar posibles errores en la recopilación de datos o valores atípicos en el conjunto de datos.</font></font></td></tr><tr class="border-t-neutral-600 first:border-t-0 border-t"><td class="p-4"><code dir="ltr" class="bg-neutral-700 mb-6 text-blue-250 py-1 px-1.5">Diagnostic</code></td><td class="p-4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">El análisis diagnóstico aclara las causas, los efectos y las interacciones de las condiciones. Hacerlo proporciona información que se obtiene a través de correlaciones e interpretación. Debemos adoptar una visión retrospectiva, similar al análisis descriptivo, con la sutil diferencia de que tratamos de encontrar razones para los acontecimientos y desarrollos.</font></font></td></tr><tr class="border-t-neutral-600 first:border-t-0 border-t"><td class="p-4"><code dir="ltr" class="bg-neutral-700 mb-6 text-blue-250 py-1 px-1.5">Predictive</code></td><td class="p-4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Al evaluar datos históricos y actuales, el análisis predictivo crea un modelo predictivo de probabilidades futuras. Basado en los resultados de análisis descriptivos y diagnósticos, este método de análisis de datos permite identificar tendencias, detectar desviaciones de los valores esperados en una etapa temprana y predecir sucesos futuros con la mayor precisión posible.</font></font></td></tr><tr class="border-t-neutral-600 first:border-t-0 border-t"><td class="p-4"><code dir="ltr" class="bg-neutral-700 mb-6 text-blue-250 py-1 px-1.5">Prescriptive</code></td><td class="p-4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">El análisis prescriptivo tiene como objetivo limitar qué acciones tomar para eliminar o prevenir un problema futuro o desencadenar una actividad o proceso específico.</font></font></td></tr></tbody></table></div>

---

## Inteligencia de código abierto

Supongamos que nuestro cliente quiere que veamos qué información podemos encontrar sobre su empresa en Internet. Para ello utilizamos lo que se conoce como `Open Source Intelligence` (`OSINT`). OSINT es un proceso para encontrar información disponible públicamente sobre una empresa o individuos objetivo que permite la identificación de eventos (es decir, reuniones públicas y privadas), dependencias externas e internas y conexiones. OSINT utiliza información pública (de código abierto) de fuentes disponibles gratuitamente para obtener los resultados deseados. A menudo podemos encontrar información sensible y relevante para la seguridad de las empresas y sus empleados. Por lo general, las personas que comparten dicha información desconocen que no son las únicas que pueden acceder a ella.

Es posible encontrar información altamente sensible como contraseñas, hashes, claves, tokens y mucho más que pueden darnos acceso a la red en tan solo unos minutos. Repositorios en sitios como [Github](https://github.com/) u otras plataformas de desarrollo a menudo no están configuradas correctamente y los espectadores externos pueden ver esta información. Si se encuentra este tipo de información confidencial al inicio de las pruebas, la sección Manejo de incidentes e informes del RoE debe describir el procedimiento para informar este tipo de vulnerabilidades de seguridad críticas. Las contraseñas o claves SSH publicadas públicamente representan una brecha de seguridad crítica si aún no se han eliminado o modificado. Por lo tanto, el administrador de nuestro cliente debe revisar esta información antes de continuar.

#### Claves SSH privadas y públicas

![Página de código de búsqueda que muestra un fragmento de código con claves públicas y privadas OpenSSH redactadas.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/searchcode3.png)

Los desarrolladores a menudo comparten secciones enteras de código en [Desbordamiento de pila](https://stackoverflow.com/) para mostrar a otros desarrolladores una mejor descripción general de cómo funciona su código para ayudarlos a resolver sus problemas. Este tipo de información también se puede encontrar muy rápidamente y utilizar contra la empresa. Nuestra tarea es encontrar esos agujeros de seguridad y cerrarlos. Podemos aprender mucho más de la [OSINT: Reconocimiento corporativo](https://academy.hackthebox.com/course/preview/osint-corporate-recon) módulo. Muestra muchas técnicas diferentes sobre cómo podemos encontrar dicha información.

---

## Enumeración de infraestructura

Durante la enumeración de la infraestructura, intentamos obtener una visión general de la posición de la empresa en Internet y la intranet. Para ello utilizamos OSINT y los primeros escaneos activos. Utilizamos servicios como DNS para crear un mapa de los servidores y hosts del cliente y desarrollar una comprensión de cómo funcionan `infrastructure` está estructurado. Esto incluye servidores de nombres, servidores de correo, servidores web, instancias en la nube y más. Hacemos una lista precisa de hosts y sus direcciones IP y los comparamos con nuestro alcance para ver si están incluidos y listados.

En esta fase también intentamos determinar las medidas de seguridad de la empresa. Cuanto más precisa sea esta información, más fácil será disfrazar nuestros ataques (`Evasive Testing`). Pero identificar firewalls, como los firewalls de aplicaciones web, también nos brinda una excelente comprensión de qué técnicas podrían activar una alarma para nuestro cliente y qué métodos se pueden utilizar para evitar esa alarma.

Aquí tampoco importa "dónde" estemos posicionados, si estamos tratando de obtener una visión general de la infraestructura desde el exterior (`external`) o examinar la infraestructura desde el interior (`internal`) de la red. La enumeración desde dentro de la red nos brinda una buena descripción general de los hosts y servidores que podemos usar como objetivos para un `Password Spraying` ataque, en el que utilizamos una contraseña para intentar autenticarnos con tantos nombres de usuario diferentes como sea posible, con la esperanza de que un intento de autenticación exitoso nos otorgue un punto de apoyo en la red. Todos estos métodos y técnicas utilizados para este fin se analizarán con más detalle en los módulos individuales.

---

## Enumeración de servicios

En la enumeración de servicios, identificamos servicios que nos permiten interactuar con el host o servidor a través de la red (o localmente, desde una perspectiva interna). Por lo tanto, es fundamental conocer el servicio, qué `version` es, qué `information` nos proporciona, y el `reason` se puede utilizar. Una vez que entendemos los antecedentes de para qué se ha prestado este servicio, se pueden sacar algunas conclusiones lógicas que nos brinden varias opciones.

Muchos servicios tienen un historial de versiones que nos permite identificar si la versión instalada en el host o servidor está realmente actualizada o no. Esto también nos ayudará a encontrar vulnerabilidades de seguridad que permanecen en versiones anteriores en la mayoría de los casos. Muchos administradores tienen miedo de cambiar las aplicaciones que funcionan, ya que podría dañar toda la infraestructura. Por lo tanto, los administradores a menudo prefieren aceptar el riesgo de dejar abiertas una o más vulnerabilidades y mantener la funcionalidad en lugar de cerrar las brechas de seguridad.

---

## Enumeración del anfitrión

Una vez que tenemos una lista detallada de la infraestructura del cliente, examinamos cada host enumerado en el documento de alcance. Intentamos identificar cuál `operating system` se ejecuta en el host o servidor, que `services` utiliza, que `versions` de los servicios, y mucho más. Nuevamente, además de los escaneos activos, también podemos usar varios métodos OSINT para decirnos cómo se puede configurar este host o servidor.

Podemos encontrar muchos servicios diferentes, como un servidor FTP que la empresa utiliza para intercambiar datos entre empleados e incluso permite el acceso anónimo. Incluso hoy en día, hay muchos hosts y servidores que los fabricantes ya no admiten. Sin embargo, todavía se encuentran vulnerabilidades en estas versiones anteriores de sistemas operativos y servicios, que luego permanecen y ponen en peligro toda la infraestructura de nuestro cliente.

Aquí no importa si examinamos cada host o servidor externa o internamente. Sin embargo, desde el punto de vista interno, encontraremos servicios a los que muchas veces no se puede acceder desde el exterior. Por lo tanto, muchos administradores se vuelven descuidados y a menudo consideran que estos servicios son "seguros" porque no son directamente accesibles desde Internet. Por lo tanto, aquí a menudo se descubren muchas configuraciones erróneas debido a estas suposiciones o prácticas laxas. Durante la enumeración del host, intentamos determinar qué papel desempeña este host o servidor y con qué componentes de red se comunica. Además, también debemos identificar cuál `services` utiliza para este fin y en el cual `ports` ellos están ubicados.

Durante la enumeración interna del host, que en la mayoría de los casos se produce después del éxito `Exploitation` de una o más vulnerabilidades, también examinamos el host o servidor desde el interior. Esto significa que buscamos lo sensible `files`, local `services`, `scripts`, `applications`, `information`, y otras cosas que podrían almacenarse en el host. Esto también es una parte esencial de la `Post-Exploitation` fase, donde intentamos explotar y elevar privilegios.

---

## Saqueo

Otro paso esencial es `Pillaging`. Después de golpear el `Post-Exploitation` En esta etapa, se realiza un saqueo para recopilar información confidencial localmente sobre el host ya explotado, como nombres de empleados, datos de clientes y mucho más. Sin embargo, esta recopilación de información sólo se produce después de explotar el host de destino y obtener acceso a él.

La información que podemos obtener sobre los hosts explotados se puede dividir en muchas categorías diferentes y varía mucho. Esto depende del propósito del host y su posicionamiento en la red corporativa. Los administradores que toman las medidas de seguridad para estos hosts también juegan un papel importante. Sin embargo, dicha información puede mostrar la `impact` de un posible ataque a nuestro cliente y ser utilizado para pasos posteriores `escalate our privileges` o `move laterally` más adelante en la red.

- Tenga en cuenta que `HTB Academy` no tiene un módulo enfocado explícitamente al saqueo.

Esto es intencional por razones que aclararemos aquí. El saqueo por sí solo no es una etapa o una subcategoría como muchos suelen describir, sino una parte integral de las etapas de recopilación de información y escalada de privilegios que inevitablemente se realiza localmente en los sistemas objetivo.

- `Pillaging is explained in other modules separately, where we consider the corresponding steps valuable and necessary.`

Aquí hay una pequeña lista de módulos donde `Pillaging` Se trata, pero este tema también se tratará en muchos otros módulos:

|  |  |  |
| --- | --- | --- |
| `Network Enumeration with Nmap` | `Getting Started` | `Password Attacks` |
| `Active Directory Enumeration & Attacks` | `Linux Privilege Escalation` | `Windows Privilege Escalation` |
| `Attacking Common Services` | `Attacking Common Applications` | `Attacking Enterprise Networks` |

Interactuaremos con más de `150 targets` durante el Penetration Tester Job Role Path y realizar nueve mini pruebas de penetración simuladas, lo que nos brinda muchas oportunidades para trabajar y practicar este tema. Además, los módulos específicos del sistema operativo deben considerarse desde el punto de vista del saqueo porque gran parte de lo que se muestra en esos módulos se puede utilizar para la recuperación de información o la escalada de privilegios en los sistemas de destino.