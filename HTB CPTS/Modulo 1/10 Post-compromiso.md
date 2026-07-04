---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/944"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Post-compromiso

De la misma manera que hay un trabajo preliminar considerable antes de que comience oficialmente un compromiso (cuando comienzan las pruebas), debemos realizar muchas actividades (muchas de ellas contractualmente vinculantes) después de que se completen nuestros escaneos, explotación, movimiento lateral y actividades posteriores a la explotación. No hay dos compromisos iguales, por lo que estas actividades pueden diferir ligeramente, pero generalmente deben realizarse para cerrar un compromiso por completo.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process.png)

---

## Limpieza

Una vez completadas las pruebas, debemos realizar cualquier limpieza necesaria, como eliminar herramientas/scripts cargados en los sistemas de destino, revertir cualquier cambio de configuración (menor) que hayamos realizado, etc. Debemos tener notas detalladas de todas nuestras actividades, lo que hace que cualquier actividad de limpieza sea fácil y eficiente. Si no podemos acceder a un sistema donde es necesario eliminar un artefacto o revertir otro cambio, debemos alertar al cliente y enumerar estos problemas en los apéndices del informe. Incluso si podemos eliminar cualquier archivo cargado y revertir los cambios (como agregar una cuenta de administrador local), debemos documentar estos cambios en los apéndices de nuestro informe en caso de que el cliente reciba alertas de que necesita realizar un seguimiento y confirmar que la actividad en cuestión fue parte de nuestras pruebas autorizadas.

---

## Documentación y presentación de informes

Antes de completar la evaluación y desconectarnos de la red interna del cliente o enviar correos electrónicos de notificación de "detención" para señalar el final de la prueba (lo que significa que no habrá más interacción con los hosts del cliente), debemos asegurarnos de tener la documentación adecuada para todos los hallazgos que planeamos incluir en nuestro informe. Esto incluye salida de comandos, capturas de pantalla, una lista de hosts afectados y cualquier otra cosa específica del entorno o hallazgo del cliente. También debemos asegurarnos de haber recuperado todos los resultados de escaneo y registro si el cliente alojó una máquina virtual en su infraestructura para una prueba de penetración interna y cualquier otro dato que pueda incluirse como parte del informe o como documentación complementaria. No debemos conservar ninguna información de identificación personal (PII), información potencialmente incriminatoria,u otros datos confidenciales que encontramos durante las pruebas.

Ya deberíamos tener una lista detallada de los hallazgos que incluiremos en el informe y todos los detalles necesarios para adaptar los hallazgos al entorno del cliente. Nuestro informe entregable (que se trata en detalle en el [Documentación e informes](https://academy.hackthebox.com/module/details/162) módulo) debe constar de lo siguiente:

- Una cadena de ataque (en caso de compromiso interno total o acceso externo a interno) que detalla los pasos tomados para lograr el compromiso
- Un resumen ejecutivo sólido que una audiencia no técnica puede entender
- Hallazgos detallados específicos del entorno del cliente que incluyen una calificación de riesgo, búsqueda de impacto, recomendaciones de remediación y referencias externas de alta calidad relacionadas con el problema
- Pasos adecuados para reproducir cada hallazgo para que el equipo responsable de la remediación pueda comprender y probar el problema mientras implementa soluciones
- Recomendaciones a corto, mediano y largo plazo específicas para el medio ambiente
- Apéndices que incluyen información como el alcance de destino, datos OSINT (si son relevantes para la interacción), análisis de descifrado de contraseñas (si son relevantes), puertos/servicios descubiertos, hosts comprometidos, cuentas comprometidas, archivos transferidos a sistemas propiedad del cliente, cualquier creación de cuenta/modificaciones del sistema, un análisis de seguridad de Active Directory (si es relevante), datos de escaneo relevantes/documentación complementaria, y cualquier otra información necesaria para explicar con más detalle un hallazgo o recomendación específica

En esta etapa, crearemos un borrador de informe que será el primer entregable que recibirá nuestro cliente. Desde aquí podrán comentar el informe y solicitar cualquier aclaración/modificación necesaria.

---

## Reunión de revisión del informe

Una vez entregado el borrador del informe y el cliente ha tenido la oportunidad de distribuirlo internamente y revisarlo en profundidad, es habitual celebrar una reunión de revisión del informe para revisar los resultados de la evaluación. La reunión de revisión del informe generalmente incluye a las mismas personas del cliente y de la empresa que realiza la evaluación. Dependiendo de los tipos de hallazgos, el cliente puede contratar expertos técnicos adicionales si el hallazgo está relacionado con un sistema o aplicación del que es responsable. Por lo general, no leeremos el informe completo palabra por palabra, sino que analizaremos brevemente cada hallazgo y daremos una explicación desde nuestra propia perspectiva/experiencia. El cliente tendrá la oportunidad de hacer preguntas sobre cualquier tema del informe, pedir aclaraciones o señalar cuestiones que necesiten ser corregidas.A menudo, el cliente vendrá con una lista de preguntas sobre hallazgos específicos y no querrá cubrir todos los hallazgos en detalle (como los de bajo riesgo).

---

## Aceptación entregable

El alcance del trabajo debe definir claramente la aceptación de los resultados de cualquier proyecto. En las evaluaciones de pruebas de penetración, generalmente, entregamos un informe marcado `DRAFT` y darle al cliente la oportunidad de revisar y comentar. Una vez que el cliente haya enviado comentarios (es decir, respuestas de la gerencia, solicitudes de aclaración/cambios, evidencia adicional, etc.) ya sea por correo electrónico o (idealmente) durante una reunión de revisión del informe, podemos emitirles una nueva versión del informe marcada `FINAL`. Algunas firmas de auditoría a las que los clientes pueden estar en deuda no aceptarán un informe de prueba de penetración con un `DRAFT` designación. A otras empresas no les importará, pero lo mejor es mantener un enfoque uniforme para todos los clientes.

---

## Pruebas posteriores a la remediación

La mayoría de los compromisos incluyen pruebas posteriores a la remediación como parte del costo total del proyecto. En esta fase, revisaremos cualquier documentación proporcionada por el cliente que muestre evidencia de remediación o simplemente una lista de hallazgos remediados. Necesitaremos volver a acceder al entorno objetivo y probar cada problema para asegurarnos de que se haya solucionado adecuadamente. Emitiremos un informe posterior a la remediación que muestre claramente el estado del medio ambiente antes y después de las pruebas posteriores a la remediación. Por ejemplo, podemos incluir una tabla como:

| # | Encontrar la gravedad | Encontrar título | Estado |
| --- | --- | --- | --- |
| 1 | Alto | Inyección SQL | Remediado |
| 2 | Alto | Autenticación rota | Remediado |
| 3 | Alto | Carga de archivos sin restricciones | Remediado |
| 4 | Alto | Filtrado de salida y web inadecuado | No remediado |
| 5 | Medio | La firma de SMB no está habilitada | No remediado |
| 6 | Bajo | Listado de directorios habilitado | No remediado |

Para cada hallazgo (cuando sea posible), querremos mostrar evidencia de que el problema ya no está presente en el entorno a través de la salida de escaneo o prueba de que las técnicas de explotación originales fallan.

---

## El papel del pentester en la remediación

Dado que una prueba de penetración es esencialmente una auditoría, debemos seguir siendo terceros imparciales y no realizar remediaciones sobre nuestros hallazgos (como corregir código, parchar sistemas o realizar cambios de configuración en Active Directory). Debemos mantener cierto grado de independencia y podemos actuar como asesores confiables brindando asesoramiento general sobre cómo se podría solucionar un problema específico o estar disponible para explicar/demostrar más a fondo un hallazgo para que el equipo asignado para remediarlo lo comprenda mejor. No deberíamos implementar cambios nosotros mismos ni siquiera brindar consejos de remediación precisos (es decir, para la inyección SQL, podemos decir "desinfectar la entrada del usuario" pero no darle al cliente un fragmento de código reescrito). Esto ayudará a mantener la integridad de la evaluación y no introducirá ningún posible conflicto de intereses en el proceso.

---

## Retención de datos

Una vez concluida una prueba de penetración, tendremos una cantidad considerable de datos específicos del cliente, como resultados de escaneo, salida de registro, credenciales, capturas de pantalla y más. Los requisitos de retención y destrucción de datos pueden diferir de un país a otro y de una empresa a otra, y los procedimientos relacionados con cada uno deben describirse claramente en el lenguaje del contrato del Alcance del Trabajo y las Reglas de Compromiso. Por [Guía para pruebas de penetración](https://www.pcisecuritystandards.org/documents/Penetration_Testing_Guidance_March_2015.pdf) del estándar de seguridad de datos PCI (PCI DSS):

"Si bien actualmente no existen requisitos PCI DSS con respecto a la retención de evidencia recopilada por el Probador de penetración, es una mejor práctica recomendada que el probador conserve dicha evidencia (ya sea interno a la organización o a un proveedor externo) por un período de tiempo mientras se considera cualquier leyes locales, regionales o de empresa que deben seguirse para la retención de pruebas. Esta evidencia debería estar disponible previa solicitud de la entidad objetivo u otras entidades autorizadas según se define en las reglas de compromiso."

Debemos conservar la evidencia durante algún tiempo después de la prueba de penetración en caso de que surjan preguntas sobre hallazgos específicos o para ayudar a volver a probar los hallazgos "cerrados" después de que el cliente haya realizado actividades de remediación. Cualquier dato retenido después de la evaluación debe almacenarse en una ubicación segura propiedad de la empresa y controlada por ella y cifrarse en reposo. Todos los datos deben borrarse de los sistemas de prueba al concluir una evaluación. Se debe crear una nueva máquina virtual específica para el cliente en cuestión para cualquier prueba posterior a la remediación o investigación de hallazgos relacionados con las consultas del cliente.

---

## Cerrar

Una vez que hayamos entregado el informe final, ayudado al cliente con preguntas sobre la remediación y realizado pruebas posteriores a la remediación/emitido un nuevo informe, finalmente podremos cerrar el proyecto. En esta etapa, debemos asegurarnos de que todos los sistemas utilizados para conectarnos a los sistemas del cliente o procesar datos hayan sido borrados o destruidos y que todos los artefactos sobrantes de la interacción se almacenen de forma segura (encriptados) según la política de nuestra empresa y según las obligaciones contractuales con nuestro cliente. Los pasos finales serían facturar al cliente y cobrar el pago por los servicios prestados. Por último, siempre es bueno hacer un seguimiento con una encuesta de satisfacción del cliente posterior a la evaluación para que el equipo y la gerencia, en particular,Se puede ver lo que salió bien durante el compromiso y lo que se podría mejorar desde el punto de vista del proceso de la empresa y del consultor individual asignado al proyecto. Es posible que surjan discusiones sobre trabajos de seguimiento en las semanas o meses posteriores si el cliente está satisfecho con nuestro trabajo y nuestras interacciones diarias.

A medida que aumentamos continuamente nuestras habilidades técnicas, siempre debemos buscar formas de mejorar nuestras habilidades interpersonales y convertirnos en consultores profesionales más completos. Al final, el `client will usually remember interactions` durante la evaluación, comunicación y cómo fueron tratados/valorados por la empresa que contratan, `not the fancy exploit chain the pentester pulled off to pwn their systems`. Tómese este tiempo para reflexionar sobre sí mismo y trabajar en la mejora continua en todos los aspectos de su función como probador de penetración profesional.