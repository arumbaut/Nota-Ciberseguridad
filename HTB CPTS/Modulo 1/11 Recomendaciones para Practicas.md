---
title: "Academia Hack The Box"
source: "https://academy.hackthebox.com/app/module/90/section/945"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Práctica

---

Todas las teorías del mundo no nos serán de ninguna utilidad si no podemos transferirlas a la práctica y aplicar nuestro conocimiento a situaciones prácticas del mundo real. Poner en uso con frecuencia las Tácticas, Técnicas y Procedimientos (TTP) que hemos cubierto en el camino del Probador de Penetración es lo mejor que podemos hacer para mantener nuestras habilidades actualizadas y garantizar que cuando llegue el momento de ponerlas a trabajar en el entorno de un cliente, estemos seguros de nosotros mismos y del impacto potencial que nuestras acciones pueden tener. Sin embargo, las habilidades técnicas son sólo la mitad de la batalla. También necesitamos excelentes habilidades de comunicación escrita y verbal para ser evaluadores de penetración eficaces. Esto incluye cosas aparentemente menores, como poder escribir un correo electrónico claro y profesional y presentar y defender nuestro trabajo durante una reunión con un cliente y a través de un informe profesional.

A menudo te encontrarás trabajando con un equipo en este campo y, como equipo, podemos ayudarnos unos a otros a crecer y perfeccionar nuestras habilidades. ¿Necesitas practicar cómo dirigir una llamada inicial con un cliente? Haga que un amigo o compañero de equipo actúe como un cliente ficticio. Utilice ese tiempo para practicar cómo hacer sus preguntas iniciales sobre el alcance y definir el pentest que espera ofrecer. Estas mismas acciones se pueden utilizar al practicar la entrega de su tutorial posterior al informe de compromiso para un cliente.

Las pruebas de penetración son divertidas. Podemos atacar una red y actuar como piratas informáticos del mundo real durante un período de tiempo. Sin embargo, lo que a algunas personas puede resultarles aburrido es una parte esencial: documentación exhaustiva y sólidas habilidades periodísticas. Un cliente no podrá hacer mucho con un informe vago de dos páginas (de la misma manera que un módulo de dos secciones no le serviría de mucho). Si fuimos contratados por una empresa Fortune 500 y pudimos tomar el control de todo su dominio sin activar una alarma, necesitaremos poder demostrarlo. Si no podemos respaldar nuestras afirmaciones con pruebas claras, perderemos credibilidad y nuestro trabajo será puesto en duda.

De manera similar, si tenemos 50+ páginas de documentación, tenemos considerablemente más evidencia para respaldar nuestro trabajo y es más probable que causemos una impresión en los tomadores de decisiones de la empresa cliente. Dicho esto, si nuestra presentación es descuidada y el informe es difícil de seguir o no profundiza en los pasos de reproducción de la vulnerabilidad y ofrece recomendaciones claras de remediación, o el resumen ejecutivo está mal escrito, nuestro arduo trabajo no será bien recibido. La documentación y los informes (incluido cómo redactar un informe de alta calidad) se tratarán en otro módulo. Este módulo también ofrece muchas sugerencias y recursos para practicar esta habilidad blanda crítica.

> [!primary] Primary
> Nota: Cuando trabajamos en un equipo de pentest, a menudo practicábamos llamadas de inicio de clientes e informábamos reuniones de revisión entre nosotros. Practicamos la revisión de los resultados y nos instruimos mutuamente sobre el contenido de nuestro informe y las recomendaciones que dimos a nuestros clientes. Cuando nuestros clientes hacían preguntas o cuestionaban nuestras recomendaciones, estábamos preparados para manejar la situación y podíamos responder claramente en el momento por qué recomendaríamos una solución específica. Este tipo de práctica seguramente te dará un aspecto más pulido y profesional.

Por más cruciales que sean las partes de una prueba de penetración orientadas al cliente, no importarán mucho si no practicamos nuestras habilidades prácticas con el teclado. Practicar nos ayudará a ver qué nos resulta natural y qué áreas debemos mejorar. La lectura no reemplaza la práctica práctica (aunque la teoría escrita es crucial para desarrollar una comprensión profunda de la gran variedad de temas que cubrimos). Una vez que ciertas tareas se conviertan en algo natural a través de una práctica considerable, ahorraremos tiempo y energía que podremos utilizar para profundizar en las evaluaciones de los clientes o para nuestra propia investigación y análisis.

Podemos ser magos en la explotación web, pero tenemos dificultades cuando nos enfrentamos a un entorno de Active Directory. Lo ideal es que practiques en entornos de laboratorio que coincidan con los de tus clientes. (Si a menudo realiza pruebas contra organizaciones que utilizan equipos específicos, como el campo médico, lo ideal es que tenga réplicas de dispositivos comunes con los que pueda encontrarse para realizar pruebas) Pero eso no siempre es factible. Entonces, ¿qué puedes hacer? Bueno, en Hack The Box tenemos muchas formas diferentes de perfeccionar tus habilidades. Todo, desde máquinas hasta desafíos y desde Sherlocks hasta Pro Labs, se puede utilizar para obtener más experiencia práctica al lidiar con todas las clases de vulnerabilidades. Los módulos aquí en HTB Academy brindan un excelente recurso para practicar nuestras habilidades. Muchos de los módulos de Penetration Tester Job Role Path cuentan con laboratorios a los que se puede acceder como pruebas de penetración simuladas.Esta repetición puede resultar tediosa al principio, pero ahorrará innumerables horas que podremos utilizar para seguir mejorando. Los pasos a continuación pueden ayudarnos a guiarnos en el camino hacia la práctica de lo que hemos aprendido:

---

## Pasos de práctica

Piensa en las habilidades que has adquirido y qué es lo que más te interesa de ellas. A partir de ahí, podemos elegir algunos módulos más para aumentar nuestro conocimiento, máquinas para practicar y Pro Labs o Endgames para ponernos realmente a prueba. Los números a continuación son un buen ejemplo inicial:

- 2x Módulos
- 3 máquinas retiradas
- 5 máquinas activas
- 1x Laboratorio profesional / Endgame

#### Módulos

Los módulos elegidos deben categorizarse según `two different difficulties`: `technical` y `offensive`. Los utilizamos para familiarizarnos con los ataques y las posibilidades y desarrollar una imagen y comprensión precisas de esos ataques. Luego utilizamos los ejercicios proporcionados y sus máquinas para aprender a aplicar estas técnicas y, al mismo tiempo, crear métodos eficientes `notes` y `screenshots` para mayor precisión ` documentation`. A continuación se muestra un buen plan para abordar un módulo:

| **Paso** | **Tarea** |
| --- | --- |
| 1. | Lea el módulo |
| 2. | Practica los ejercicios |
| 3. | Completa el módulo |
| 4. | Comience los ejercicios del módulo desde cero |
| 5. | Mientras resuelves nuevamente los ejercicios, toma notas |
| 6. | Crear documentación técnica basada en las notas |
| 7. | Crear documentación no técnica basada en las notas |

La selección de varios módulos nos permite abordar diferentes tecnologías y problemas que podamos enfrentar. Descubriremos varios aspectos que deben considerarse y, a veces, documentarse/anotarse con más detalle que antes. Estas notas serán muy valiosas a medida que avancemos en nuestras carreras. Algunas combinaciones de tecnologías y vectores de ataque pueden ser raras de ver en la naturaleza, por lo que tener notas detalladas sobre esos sistemas desde el momento en que interactuó con ellos lo ayudará a avanzar más rápido en una evaluación donde los encuentre.

Después de completar el módulo, debemos crear uno menor `technical` y `non-technical` documentación (es decir, crear ejemplos de hallazgos técnicos y pasos de reproducción y entradas de resumen ejecutivo que podrían incluirse en un informe). Concéntrese en practicar la creación de documentación "lista para el cliente". Mucha gente subestima la cantidad de conocimientos y habilidades que quedan impresos a través de la creación de la documentación. Practicar la redacción de documentación puede ayudarnos a consolidar algunos temas en nuestras mentes y facilitarnos la explicación de conceptos tanto a audiencias técnicas como no técnicas.

#### Máquinas retiradas

Cuando hayamos completado (al menos) dos módulos y estemos satisfechos con nuestras notas y documentación, podremos seleccionar tres máquinas retiradas diferentes. Estos también deberían diferir en dificultad, pero recomendamos elegir `two easy` y `one medium` máquinas. Al final de cada módulo, encontrará máquinas retiradas recomendadas a considerar que lo ayudarán a practicar las herramientas y temas específicos cubiertos en el módulo. Estos hosts compartirán uno o más vectores de ataque vinculados al módulo.

Con las máquinas retiradas, tenemos una ventaja significativa porque podemos encontrar artículos existentes en línea de muchos autores diferentes (todos con diferentes enfoques) con los que podemos comparar nuestras notas. Si optamos por comprar una membresía VIP en la plataforma principal de HTB, también tendremos acceso a artículos oficiales de HTB que presentan otro punto de vista y, a menudo, incluyen algunas consideraciones defensivas. Podemos utilizar estos artículos para comparar si hemos anotado todo lo necesario y no hemos pasado por alto nada. El orden en el que podemos proceder a practicar con las máquinas retiradas se parece a este:

| **Paso** | **Tarea** |
| --- | --- |
| 1. | Obtenga la bandera del usuario por su cuenta |
| 2. | Consigue la bandera raíz por tu cuenta |
| 3. | Escribe tu documentación técnica |
| 4. | Escribe tu documentación no técnica |
| 5. | Compara tus notas con el artículo oficial (o un artículo comunitario si no tienes una suscripción VIP) |
| 6. | Crea una lista de la información que te has perdido |
| 7. | Ver [De Ippsec](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA) Tutorial y compáralo con tus notas |
| 8. | Amplíe sus notas y documentación agregando las partes faltantes |

Por último, deberíamos crear `technical` y `non-technical` documentación de nuevo. Descubriremos que éste probablemente será más extenso que los anteriores porque estamos trabajando con muchos más temas que necesitamos cubrir y documentar aquí. La ventaja más significativa de este enfoque es que pasamos por todo el proceso de pruebas de penetración, mejorando la forma en que capturamos información esencial y tenemos todo lo que necesitamos para preparar nuestra documentación basada en nuestras experiencias y notas.

#### Máquinas activas

After building a good foundation with the modules and the retired machines, we can venture to `two easy`, `two medium`, and `one hard` active machine. We can also take these from the corresponding module recommendations at the end of each module in Academy.

The advantage of this method is that we simulate as realistic a situation as possible using a single host that we have no familiarity with and cannot find documentation on (blackbox approach). As long as the machine remains active, no official write-ups will be published. This means that we cannot check whether we have everything or whether we have missed something from any official source. This puts us in the situation of relying on ourselves and our abilities. Ideal practice steps for active machines would look like this:

| **Step** | **Task** |
| --- | --- |
| 1. | Get the user and root flag |
| 2. | Write your technical documentation |
| 3. | Write your non-technical documentation |
| 4. | Have it proofread by technical and non-technical persons |

Proofreading gives us our first impressions of how the readers receive the two types of documentation. This gives us an idea of which aspects of our documentation need to be improved for both technical and non-technical audiences. As we can already imagine, not many non-technical people are interested in reading this type of documentation. Therefore, we need to design the non-technical documentation to be `informative`, `high quality`, and kept `concise` but meaningful and free of highly technical jargon. More about this is covered in the [Documentation & Reporting](https://academy.hackthebox.com/module/details/162) module.

#### Pro Lab/Endgame

Once we feel comfortable going against singular hosts and documenting our findings, we can take on Pro Labs and Endgames. These labs are large multi-host environments that often simulate enterprise networks of varying sizes similar to those we could run into during actual penetration tests for our clients. This will present us with different challenges than we are used to. We will no longer be focusing on a single host and now have to consider how the different hosts interact with each other. These interactions will make for new and interesting vectors we can potentially practice against as well. For example, running a tool like `Responder` in an Active Directory environment to see traffic and capture a user's password hash or some sort of user interaction is much more likely in a simulated network than when attacking a single box. Attacking infrastructure with several interconnected hosts and network components will create additional connections we need to consider in our documentation. Instead of showing how to complete a single host from start to finish, we will need to practice writing up an entire attack chain, showing our path from foothold to network compromise. This, again, is covered in the `Documentation & Reporting` module. The practice we have from the previous tasks will make this much easier for us as everything builds on each other.

---

## Wrapping Up

We have covered a considerable amount of information in this module. If you are just beginning the `Penetration Tester` Job Role path, we recommend continuing in the order in which the modules are presented. If we are new to all this, skipping around could lead to gaps in knowledge and make certain modules difficult to finish without prerequisite knowledge. If you are already partially through the path, it's worth going back through modules that you have already completed and consider the various steps in the context of the penetration testing process presented in this module.

La práctica y la mejora continuas son vitales independientemente de dónde te encuentres en tu viaje. Podemos mejorar continuamente nuestra metodología actual, aprender cosas de manera diferente y aprender nuevos conceptos. El campo de la tecnología de la información cambia rápidamente. Con frecuencia se descubren nuevos ataques y debemos estar al tanto de los últimos y mejores TTP para ser lo más efectivos posible y brindar a nuestros clientes la información necesaria para ayudar a proteger sus entornos de un panorama de amenazas en constante evolución. Nunca dejes de aprender y mejorar. Desafíate a ti mismo diariamente. Toma descansos. Disfruta del viaje y no lo olvides `Think Outside The Box`!