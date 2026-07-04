---
title: "Prueba de concepto | Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/943"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Prueba de concepto

---

`Proof of Concept` (`PoC`) o `Proof of Principle` es un término de gestión de proyectos. En la gestión de proyectos, sirve como prueba de que un proyecto es factible en principio. Los criterios para ello pueden residir en factores técnicos o comerciales. Por lo tanto, es la base para seguir trabajando, en nuestro caso, en los pasos necesarios para proteger la red corporativa confirmando las vulnerabilidades descubiertas. En otras palabras, sirve como base para la toma de decisiones sobre el curso de acción futuro. Al mismo tiempo, permite identificar y minimizar los riesgos.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-POC.png)

Este paso del proyecto a menudo se integra en el proceso de desarrollo de nuevo software de aplicación (creación de prototipos) o soluciones de seguridad de TI. Para nosotros en seguridad de la información, aquí es donde demostramos vulnerabilidades en sistemas operativos o software de aplicación. Utilizamos este PoC para demostrar que existe un problema de seguridad para que los desarrolladores o administradores puedan validarlo, reproducirlo, ver el impacto y probar sus esfuerzos de remediación. Uno de los ejemplos más comunes utilizados para demostrar vulnerabilidades de software es ejecutar la calculadora (calc.exe en Windows) en el sistema de destino. En principio, el PoC también evalúa la probabilidad de éxito del acceso al sistema a partir de la explotación real.

A `PoC` Puede tener muchas representaciones diferentes. Por ejemplo, `documentation` de las vulnerabilidades encontradas también puede constituir un PoC. La versión más práctica de un PoC es una `script` o `code` que explota automáticamente las vulnerabilidades encontradas. Esto demuestra la explotación impecable de las vulnerabilidades. Esta variante es sencilla para un administrador o desarrollador porque puede ver qué pasos sigue nuestro script para explotar la vulnerabilidad.

Sin embargo, hay una desventaja importante que se ha producido de vez en cuando. Una vez que los administradores y desarrolladores han recibido dicho script de nuestra parte, les resulta fácil "luchar" contra nuestro script. Se centran en cambiar los sistemas para que el script que creamos ya no funcione. Lo importante es que el guión es único `one way` de explotar una vulnerabilidad determinada. Por lo tanto, trabajar contra nuestro script en lugar de con él y modificar y proteger los sistemas para que nuestro script ya no funcione no significa que la información obtenida del script no pueda obtenerse de otra manera. Es un aspecto importante que debe discutirse con los administradores y desarrolladores y mencionarse y señalarse explícitamente.

El informe que reciban de nosotros debería ayudarles a ver el panorama completo, centrarse en cuestiones más amplias y ofrecerles consejos claros para remediarlo. Incluir un tutorial de la cadena de ataques en caso de compromiso del dominio durante una evaluación interna es una excelente manera de mostrar cómo se pueden combinar múltiples fallas y cómo solucionar una falla romperá la cadena, pero las otras fallas seguirán existiendo. Si estos tampoco se solucionan, puede haber otro camino para llegar al punto donde se remedió la cadena de ataque y continuar. También deberíamos dejar claro este punto durante nuestra reunión de revisión del informe.

Por ejemplo, si un usuario utiliza la contraseña `Password123`, la vulnerabilidad subyacente no es la contraseña sino la `password policy`. Si se descubre que un administrador de dominio está usando esa contraseña y se cambia, esa cuenta ahora tendrá una contraseña más segura, pero el problema de las contraseñas débiles probablemente seguirá siendo endémico dentro de la organización.

Si la política de contraseñas siguiera estándares elevados, el usuario no podría utilizar una contraseña tan débil. Los administradores y desarrolladores son responsables de la funcionalidad y la calidad de sus sistemas y aplicaciones. Además, la alta calidad significa altos estándares, lo cual debemos enfatizar a través de nuestras recomendaciones de remediación.