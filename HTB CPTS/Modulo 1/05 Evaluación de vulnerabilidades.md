---
title: "Evaluación de vulnerabilidades | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/939"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Evaluación de vulnerabilidades

---

Durante el `vulnerability assessment` fase, examinamos y analizamos la información recopilada durante la fase de recopilación de información. La fase de evaluación de la vulnerabilidad es un proceso analítico basado en los hallazgos.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-VA.png)

`An analysis is a detailed examination of an event or process, describing its origin and impact, that with the help of certain precautions and actions, can be triggered to support or prevent future occurrences.`

Cualquier análisis puede resultar muy complicado, ya que muchos factores diferentes y sus interdependencias juegan un papel importante. Aparte de que trabajamos con los tres tiempos diferentes (pasado, presente y futuro) durante cada análisis, el origen y el destino juegan un papel importante. Hay cuatro tipos diferentes de análisis:

| **Tipo de análisis** | **Descripción** |
| --- | --- |
| `Descriptive` | El análisis descriptivo es esencial en cualquier análisis de datos. Por un lado, describe un conjunto de datos basado en características individuales. Ayuda a detectar posibles errores en la recopilación de datos o valores atípicos en el conjunto de datos. |
| `Diagnostic` | El análisis diagnóstico aclara las causas, los efectos y las interacciones de las condiciones. Hacerlo proporciona información que se obtiene a través de correlaciones e interpretación. Debemos adoptar una visión retrospectiva, similar al análisis descriptivo, con la sutil diferencia de que tratamos de encontrar razones para los acontecimientos y desarrollos. |
| `Predictive` | Al evaluar datos históricos y actuales, el análisis predictivo crea un modelo predictivo de probabilidades futuras. Basado en los resultados de análisis descriptivos y diagnósticos, este método de análisis de datos permite identificar tendencias, detectar desviaciones de los valores esperados en una etapa temprana y predecir sucesos futuros con la mayor precisión posible. |
| `Prescriptive` | El análisis prescriptivo tiene como objetivo limitar qué acciones tomar para eliminar o prevenir un problema futuro o desencadenar una actividad o proceso específico. |

Utilizamos nuestros resultados e información obtenida hasta el momento y los analizamos para sacar conclusiones. La formación de conclusiones puede extenderse mucho, pero luego debemos confirmarlas o refutarlas. Supongamos que encontramos un puerto TCP abierto 2121 en un host durante la fase de recopilación de información.

Aparte del hecho de que este puerto está abierto, Nmap no nos mostró nada más. Ahora debemos preguntarnos qué conclusiones se pueden sacar de este resultado. Por lo tanto, no importa con qué pregunta empecemos para sacar nuestras conclusiones. Sin embargo, es fundamental preguntar `precise questions` y recuerda lo que nosotros `know` y `do not know`. En este punto, primero debemos preguntarnos qué es lo que hacemos `see` y lo que realmente hacemos `have`, porque lo que vemos no es lo mismo que lo que tenemos:

- a `TCP` puerto `2121`. - `TCP` ya significa que este servicio lo es `connection-oriented`.
- ¿Es esto un `standard` ¿puerto?- `No`, porque estos están entre `0-1023`, también conocido o [puertos del sistema](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
- ¿Hay algún número en esto `port number` esa mirada `familiar`?- `Yes`, `TCP` puerto `21` (`FTP`). A partir de nuestra experiencia, conoceremos muchos puertos estándar y sus servicios, que los administradores a menudo intentan disfrazar, pero a menudo utilizan alternativas "fáciles de recordar".

Según nuestra suposición, podemos intentar conectarnos al servicio usando `Netcat` o un `FTP` cliente e intentar establecer una conexión para confirmar o refutar nuestra suposición.

Al conectarnos al servicio, notamos que la conexión tardó más de lo habitual (unos 15 segundos). Hay algunos servicios cuya velocidad de conexión o tiempo de respuesta se puede configurar. Ahora que sabemos que un servidor FTP se está ejecutando en este puerto, podemos deducir el origen de nuestro escaneo "fallido". Podríamos confirmarlo nuevamente especificando el mínimo `probe round trip time` (`--min-rtt-timeout`) en Nmap durante 15 o 20 segundos y volviendo a ejecutar el escaneo.

---

## Investigación y análisis de vulnerabilidades

`Information Gathering` y `Vulnerability Research` Puede considerarse parte del análisis descriptivo. Aquí es donde identificamos los componentes individuales de la red o del sistema que estamos investigando. En `Vulnerability Research`, buscamos vulnerabilidades conocidas, exploits y agujeros de seguridad que ya han sido descubiertos y reportados. Por lo tanto, si hemos identificado una versión de un servicio o aplicación a través de la recopilación de información y hemos encontrado una [Vulnerabilidades y exposiciones comunes (CVE)](https://www.cve.org/ResourcesSupport/FAQs), es muy probable que esta vulnerabilidad todavía esté presente.

Podemos encontrar divulgaciones de vulnerabilidades para cada componente utilizando muchas fuentes diferentes. Estos incluyen, entre otros:

|  |  |  |
| --- | --- | --- |
| [Detalles de CVE](https://www.cvedetails.com/) | [Explotar base de datos](https://www.exploit-db.com/) | [Vulneradores](https://vulners.com/) |
| [Seguridad contra tormentas de paquetes](https://packetstormsecurity.com/) | [NIST](https://nvd.nist.gov/vuln/search?execution=e2s1) |  |

Aquí es donde `Diagnostic Analysis` y `Predictive Analysis` se utiliza. Una vez que hemos encontrado una vulnerabilidad publicada como esta, podemos diagnosticarla para determinar qué está causando o ha causado la vulnerabilidad. Aquí debemos comprender la funcionalidad del `Proof-Of-Concept` (`POC`) código o la aplicación o servicio en sí lo mejor posible, ya que muchas configuraciones manuales por parte de los administradores requerirán cierta personalización para el POC. Cada POC se adapta a un caso específico que también necesitaremos adaptar al nuestro en la mayoría de los casos.

---

## Evaluación de posibles vectores de ataque

`Vulnerability Assessment` También incluye las pruebas reales, que son parte de `Predictive Analysis`. Para ello analizamos información histórica y la combinamos con la información actual que hemos podido conocer. Si hemos recibido requisitos específicos de nivel de evasión de nuestro cliente, probamos los servicios y aplicaciones encontrados `locally` o `on the target system`. Si tenemos que realizar pruebas de forma encubierta y evitar alertas, debemos reflejar el sistema objetivo localmente con la mayor precisión posible. Esto significa que utilizamos la información obtenida durante nuestra fase de recopilación de información para replicar el sistema de destino y luego buscar vulnerabilidades en el sistema implementado localmente.

---

## El regreso

Supongamos que no podemos detectar o identificar vulnerabilidades potenciales a partir de nuestro análisis. En ese caso, volveremos a la `Information Gathering` escenario y buscar información más detallada que la que hemos recopilado hasta ahora. Es importante señalar que estas dos etapas (`Information Gathering` y `Vulnerability Assessment`) a menudo se superponen, lo que da como resultado un movimiento regular de ida y vuelta entre ellos. Veremos esto en muchos videos donde el autor está resolviendo una caja HTB o algún desafío CTF. Debemos recordar que estos desafíos a menudo se resuelven lo más rápido posible y, por lo tanto, la velocidad es más importante que la calidad. En un CTF, el objetivo es llegar a la máquina objetivo y `capture the flags` con los privilegios más altos lo más rápido posible en lugar de exponer todas las debilidades potenciales del sistema.

**`A (real) Penetration Test is not a CTF.`**

Aquí el `quality` y `intensity` de nuestra prueba de penetración y su análisis tienen la máxima prioridad porque nada es peor si nuestro cliente es hackeado exitosamente a través de un vector relativamente simple que deberíamos haber descubierto durante nuestra prueba de penetración.