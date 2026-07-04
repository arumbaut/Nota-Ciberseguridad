---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/721"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Descripción general de Infosec

---

[Seguridad informática](https://en.wikipedia.org/wiki/Information_security) (infosec) es un campo vasto. El campo ha crecido y evolucionado mucho en los últimos años. Ofrece muchas especializaciones, que incluyen, entre otras:

- Seguridad de redes e infraestructuras
- Seguridad de la aplicación
- Pruebas de seguridad
- Auditoría de sistemas
- Planificación de la continuidad del negocio
- Análisis forense digital
- Detección y respuesta a incidentes

En pocas palabras, la seguridad de la información es la práctica de proteger los datos contra accesos no autorizados, cambios, uso ilegal, interrupciones, etc. Los profesionales de la seguridad de la información también toman medidas para reducir el impacto general de cualquier incidente de este tipo.

Los datos pueden ser electrónicos o físicos y tangibles (por ejemplo, planos de diseño) o intangibles (conocimiento). Una frase común que surgirá muchas veces en nuestra carrera en seguridad de la información es proteger la "confidencialidad, integridad y disponibilidad de los datos", o la `CIA triad`.

---

## Proceso de gestión de riesgos

La protección de datos debe centrarse en la implementación eficiente pero efectiva de políticas sin afectar negativamente las operaciones comerciales y la productividad de una organización. Para lograrlo, las organizaciones deben seguir un proceso llamado `risk management process`. Este proceso implica los siguientes cinco pasos:

| Paso | Explicación |
| --- | --- |
| `Identifying the Risk` | Identificar los riesgos a los que está expuesta la empresa, como riesgos legales, ambientales, de mercado, regulatorios y de otro tipo. |
| `Analyze the Risk` | Analizar los riesgos para determinar su impacto y probabilidad. Los riesgos deben asignarse a las diversas políticas, procedimientos y procesos comerciales de la organización. |
| `Evaluate the Risk` | Evaluar, clasificar y priorizar los riesgos. Luego, la organización debe decidir aceptar (inevitable), evitar (cambiar planes), controlar (mitigar) o transferir el riesgo (asegurar). |
| `Dealing with Risk` | Eliminar o contener los riesgos lo mejor posible. Esto se gestiona interactuando directamente con las partes interesadas del sistema o proceso con el que está asociado el riesgo. |
| `Monitoring Risk` | Todos los riesgos deben ser monitoreados constantemente. Los riesgos deben ser monitoreados constantemente para detectar cualquier cambio situacional que pueda cambiar su puntaje de impacto `i.e., from low to medium or high impact`. |

Como se mencionó anteriormente, el principio central de la seguridad de la información es la garantía de la información o el mantenimiento de la misma `CIA` de datos y asegurarse de que no se vean comprometidos de ninguna manera cuando ocurra un incidente. Un incidente podría ser un desastre natural, un mal funcionamiento del sistema o un incidente de seguridad.

---

## Equipo Rojo vs. Equipo Azul

En infosec, normalmente escuchamos los términos `red team` y `blue team`. En los términos más simples, el `red team` desempeña el papel de los atacantes, mientras que el `blue team` juega el papel de los defensores.

Los equipos rojos generalmente desempeñan un papel de adversario al irrumpir en la organización para identificar cualquier debilidad potencial que los atacantes reales puedan utilizar para romper las defensas de la organización. La tarea más común en el equipo rojo son las pruebas de penetración, la ingeniería social y otras técnicas ofensivas similares.

Por otro lado, el equipo azul constituye la mayoría de los trabajos de seguridad de la información. Es responsable de fortalecer las defensas de la organización analizando los riesgos, elaborando políticas, respondiendo a amenazas e incidentes y utilizando eficazmente herramientas de seguridad y otras tareas similares.

---

## Papel de los comprobadores de penetración

Un evaluador de seguridad (probador de penetración de red, probador de penetración de aplicaciones web, equipo rojo, etc.) ayuda a una organización a identificar riesgos en sus redes externas e internas. Estos riesgos pueden incluir vulnerabilidades de redes o aplicaciones web, exposición a datos confidenciales, configuraciones incorrectas o problemas que podrían provocar daños a la reputación. Un buen evaluador puede trabajar con un cliente para identificar riesgos para su organización, brindar información sobre cómo reproducir estos riesgos y orientación sobre cómo mitigar o remediar los problemas identificados durante las pruebas.

Las evaluaciones pueden adoptar muchas formas, desde una prueba de penetración de caja blanca contra todos los sistemas y aplicaciones dentro del alcance para identificar tantas vulnerabilidades como sea posible, hasta una evaluación de phishing para evaluar el riesgo o la conciencia de seguridad de los empleados, hasta una evaluación de equipo rojo específica construida alrededor de un escenario para emular a un actor de amenazas del mundo real.

Debemos comprender el panorama más amplio de los riesgos que enfrenta una organización y su entorno para evaluar y calificar con precisión las vulnerabilidades descubiertas durante las pruebas. Una comprensión profunda del proceso de gestión de riesgos es fundamental para cualquiera que comience en la seguridad de la información.

Este módulo se centrará en cómo comenzar en pruebas de penetración y seguridad de la información desde una perspectiva práctica, específicamente seleccionando y navegando por una distribución pentest, aprendiendo sobre tecnologías comunes y herramientas esenciales, aprendiendo los niveles y los conceptos básicos de las pruebas de penetración, descifrando nuestra primera caja en HTB, cómo encontrar y pedir ayuda de manera más efectiva, problemas potenciales comunes, y cómo navegar por la plataforma Hack the Box.

Si bien este módulo utiliza la plataforma Hack The Box y máquinas deliberadamente vulnerables como ejemplos, las habilidades fundamentales mostradas se aplican a cualquier entorno.