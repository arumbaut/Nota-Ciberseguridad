---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/942"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Movimiento lateral

---

Si todo saliera bien y pudiéramos penetrar en la red corporativa (`Exploitation`) con éxito, recopile información almacenada localmente y escale nuestros privilegios (`Post-Exploitation`), luego ingresamos al `Lateral Movement` escenario. El objetivo aquí es probar lo que un atacante podría hacer dentro de toda la red. Después de todo, el objetivo principal no es sólo explotar con éxito un sistema disponible públicamente, sino también obtener datos confidenciales o encontrar todas las formas en que un atacante podría inutilizar la red. Uno de los ejemplos más comunes es [ransomware](https://www.csoonline.com/article/3236183/what-is-ransomware-how-it-works-and-how-to-remove-it.html). Si un sistema de la red corporativa está infectado con ransomware, puede propagarse por toda la red. Bloquea todos los sistemas mediante diversos métodos de cifrado, dejándolos inutilizables para toda la empresa hasta que se introduce una clave de descifrado.

En los casos más comunes, la empresa es extorsionada financieramente para obtener ganancias. A menudo, sólo en este momento las empresas se dan cuenta de lo importante que es la seguridad informática. Si hubieran tenido un buen probador de penetración que hubiera probado las cosas (y los procesos adecuados y las defensas en capas implementadas), probablemente podrían haber evitado tal situación y el daño financiero (si no legal). A menudo se olvida que en muchos países, la `CEOs are held liable` por no proteger adecuadamente los datos de sus clientes.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-LA.png)

En esta etapa queremos probar hasta dónde podemos movernos manualmente en toda la red y qué vulnerabilidades podemos encontrar desde la perspectiva interna que podrían ser explotadas. Al hacerlo, pasaremos nuevamente por varias fases:

1. Pivote
2. Pruebas evasivas
3. Recopilación de información
4. Evaluación de vulnerabilidades
5. (Privilegio) Explotación
6. Post-explotación

Como se ve en el gráfico anterior, podemos pasar a esta etapa desde el `Exploitation` y el `Post-Exploitation` escenario. A veces es posible que no encontremos una forma directa de aumentar nuestros privilegios en el sistema de destino en sí, pero tenemos formas de movernos por la red. Aquí es donde `Lateral Movement` entra en juego.

---

## Pivote

En la mayoría de los casos, el sistema que utilizamos no tendrá las herramientas para enumerar la red interna de manera eficiente. Algunas técnicas nos permiten utilizar el host explotado como proxy y realizar todos los escaneos desde nuestra máquina de ataque o VM. Al hacerlo, el sistema explotado representa y enruta todas nuestras solicitudes de red enviadas desde nuestra máquina de ataque a la red interna y sus componentes de red.

De esta manera, nos aseguramos de que aún se pueda acceder a redes no enrutables (y por lo tanto públicamente inalcanzables). Esto nos permite escanearlos en busca de vulnerabilidades y penetrar más profundamente en la red. Este proceso también se conoce como `Pivoting` o `Tunneling`.

Un ejemplo elemental podría ser que tenemos una impresora en casa a la que no se puede acceder desde Internet, pero podemos enviar trabajos de impresión desde nuestra red doméstica. Si uno de los hosts de nuestra red doméstica se ha visto comprometido, se podría aprovechar para enviar estos trabajos a la impresora. Aunque este es un ejemplo simple (e improbable), ilustra el objetivo de `pivoting`, que consiste en acceder a sistemas inaccesibles a través de un sistema intermediario.

---

## Pruebas evasivas

Además, en esta etapa, deberíamos considerar si las pruebas evasivas son parte del alcance de la evaluación. Existen diferentes procedimientos para cada táctica, que nos ayudan a disfrazar estas solicitudes para no activar una alarma interna entre los administradores y el equipo azul.

Hay muchas formas de protegerse contra el movimiento lateral, incluida la red (micro) `segmentation`, `threat monitoring`, `IPS` / `IDS`, `EDR`, etc. Para evitarlos de manera eficiente, necesitamos entender cómo funcionan y a qué responden. Luego podremos adaptar y aplicar métodos y estrategias que ayuden a evitar la detección.

---

## Recopilación de información

Antes de apuntar a la red interna, primero debemos obtener un `overview` de qué sistemas y a cuántos se puede acceder desde nuestro sistema. Es posible que esta información ya esté disponible para nosotros desde la última etapa posterior a la explotación, donde analizamos más de cerca los ajustes y configuraciones del sistema.

Regresamos a la etapa de Recopilación de Información, pero esta vez lo hacemos desde dentro de la red con una visión diferente de la misma. Una vez que hayamos descubierto todos los hosts y servidores, podremos enumerarlos individualmente.

---

## Evaluación de vulnerabilidades

La evaluación de vulnerabilidades desde el interior de la red difiere de los procedimientos anteriores. Esto se debe a que ocurren muchos más errores dentro de una red que en hosts y servidores expuestos a Internet. Aquí, el `groups` al que se le ha asignado uno y el `rights` Los diferentes componentes del sistema juegan un papel esencial. Además, es común que los usuarios compartan información y documentos y trabajen juntos en ellos.

Este tipo de información es de especial interés para nosotros a la hora de planificar nuestros ataques. Por ejemplo, si comprometemos una cuenta de usuario asignada a un grupo de desarrolladores, podemos obtener acceso a la mayoría de los recursos utilizados por los desarrolladores de la empresa. Probablemente esto nos proporcionará información interna crucial sobre los sistemas y podría ayudarnos a identificar fallas o ampliar nuestro acceso.

---

## (Privilegio) Explotación

Una vez que hayamos encontrado y priorizado estas rutas, podemos saltar al paso donde las usamos para acceder a los otros sistemas. A menudo encontramos formas de descifrar contraseñas y hashes y obtener mayores privilegios. Otro método estándar es utilizar nuestras credenciales existentes en otros sistemas. También habrá situaciones en las que ni siquiera tendremos que descifrar los hashes sino que podremos usarlos directamente. Por ejemplo, podemos utilizar la herramienta [Responder](https://github.com/lgandx/Responder) para interceptar hashes NTLMv2. Si podemos interceptar un hash de un administrador, entonces podemos usar el `pass-the-hash` técnica para iniciar sesión como administrador (en la mayoría de los casos) en múltiples hosts y servidores.

Después de todo, el `Lateral Movement` La etapa tiene como objetivo moverse a través de la red interna. Los datos y la información existentes pueden ser versátiles y, a menudo, utilizarse de muchas maneras.

---

## Post-explotación

Una vez que hemos llegado a uno o más hosts o servidores, pasamos nuevamente por los pasos de la etapa de post-explotación para cada sistema. Aquí recopilamos nuevamente información del sistema, datos de usuarios creados e información comercial que puede presentarse como evidencia. Sin embargo, debemos considerar nuevamente cómo debe manejarse esta información diferente y las reglas definidas en torno a los datos sensibles en el contrato.

Finalmente, estamos listos para pasar a la `Proof-of-Concept` fase para mostrar nuestro arduo trabajo y ayudar a nuestro cliente y a los responsables de la remediación a reproducir eficientemente nuestros resultados.