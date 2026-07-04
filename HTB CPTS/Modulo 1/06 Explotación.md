---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/90/section/940"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Explotación

---

Durante el `Exploitation` etapa, buscamos formas en que estas debilidades puedan adaptarse a nuestro caso de uso para obtener el rol deseado (es decir, un punto de apoyo, privilegios aumentados, etc.). Si queremos obtener un shell inverso, necesitamos modificar el PoC para ejecutar el código, de modo que el sistema de destino se conecte nuevamente con nosotros a través de (idealmente) una conexión cifrada a una dirección IP que especifiquemos. Por lo tanto, la preparación de un exploit es principalmente parte de la `Exploitation` escenario.

![Proceso de prueba de penetración: Pre-compromiso, Recopilación de información, Evaluación de vulnerabilidad, Explotación, Post-Explotación, Movimiento lateral, Prueba de concepto, Post-Compromiso.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/90/0-PT-Process-EX.png)

Estas etapas no deben estar estrictamente separadas entre sí, ya que están estrechamente conectadas. Sin embargo, sigue siendo importante distinguir en qué fase nos encontramos y su propósito. Porque más adelante, con procesos mucho más complejos y mucha más información, es muy fácil perder de vista los pasos que se han dado, sobre todo si la prueba de penetración dura varias semanas y cubre un alcance masivo.

---

## Priorización de posibles ataques

Una vez que hayamos encontrado una o dos vulnerabilidades durante el `Vulnerability Assessment` etapa que podemos aplicar a nuestra red/sistema objetivo, podemos priorizar esos ataques. Cuál de esos ataques priorizamos más que los demás depende de los siguientes factores:

- Probabilidad de éxito
- Complejidad
- Probabilidad de daño

Primero, debemos evaluar el `probability of successfully` ejecutar un ataque particular contra el objetivo. [Puntuación CVSS](https://nvd.nist.gov/vuln-metrics/cvss) Puede ayudarnos aquí, utilizando el [Calculadora NVD](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator) Es mejor calcular los ataques específicos y su probabilidad de éxito.

`Complexity` representa el esfuerzo de explotar una vulnerabilidad específica. Esto se utiliza para estimar cuánto tiempo, esfuerzo e investigación se requieren para ejecutar el ataque al sistema con éxito. Nuestra experiencia juega un papel importante aquí porque si vamos a llevar a cabo un ataque que nunca hemos utilizado antes, esto lógicamente requerirá mucha más investigación y esfuerzo ya que debemos comprender el ataque y la estructura de explotación en detalle antes de aplicarlo.

Estimando el `probability of damage` causado por la ejecución de un exploit juega un papel crítico, ya que debemos evitar cualquier daño a los sistemas objetivo. Generalmente, no realizamos ataques DoS a menos que nuestro cliente los requiera. Sin embargo, atacar los servicios en ejecución en vivo con exploits que pueden causar daños al software o al sistema operativo es algo que debemos evitar en todo momento.

Además, podemos asignar estos factores a un sistema de puntos personales que permitirá calcular la evaluación con mayor precisión en función de nuestras habilidades y conocimientos:

#### Ejemplo de priorización

| **Factor** | **Puntos** | **Inclusión remota de archivos** | **Desbordamiento de búfer** |
| --- | --- | --- | --- |
| 1\. Probabilidad de éxito | `10` | 10 | 8 |
| 2\. Complejidad - Fácil | `5` | 4 | 0 |
| 3\. Complejidad - Media | `3` | 0 | 3 |
| 4\. Complejidad - Dura | `1` | 0 | 0 |
| 5\. Probabilidad de daño | `-5` | 0 | \-5 |
| **Resumen** | `max. 15` | 14 | 6 |

Basándonos en el ejemplo anterior, preferiríamos el `remote file inclusion` attack. Es fácil de preparar y ejecutar y no debe causar ningún daño si se aborda con cuidado.

---

## Preparación para el ataque

A veces nos encontraremos con una situación en la que no podremos encontrar código de explotación PoC de alta calidad y que funcione. Por lo tanto, puede ser necesario reconstruir el exploit localmente en una máquina virtual que represente nuestro host de destino para determinar con precisión qué se debe adaptar y cambiar. Una vez que hayamos configurado el sistema localmente e instalado componentes conocidos para reflejar el entorno de destino lo más fielmente posible (es decir, los mismos números de versión para los servicios/aplicaciones de destino), podemos comenzar a preparar el exploit siguiendo los pasos descritos en el exploit. Luego probamos esto en una máquina virtual alojada localmente para asegurarnos de que funcione y no cause daños significativos. En otras situaciones, nos encontraremos con configuraciones erróneas y vulnerabilidades que vemos muy a menudo y sabemos exactamente qué herramienta o exploit utilizar y si el exploit o la técnica son "seguros"o puede causar inestabilidad.

Si alguna vez tiene dudas antes de ejecutar un ataque, siempre es mejor consultar con nuestro cliente, proporcionándole todos los datos necesarios para que pueda tomar una decisión informada sobre si desea que intentemos explotarlo o simplemente marcar el hallazgo como un problema. Si optan por que no procedamos con la explotación, podemos señalar en el informe que no se confirmó activamente, pero es probable que sea una cuestión que deba abordarse. Tenemos cierto margen de maniobra durante las pruebas de penetración y siempre debemos utilizar nuestro mejor criterio si un ataque en particular parece demasiado riesgoso o podría causar una interrupción. En caso de duda, comunícate. Es casi seguro que el líder/gerente de su equipo, el cliente, preferirá una comunicación adicional antes que encontrarse con una situación en la que intenten volver a poner un sistema en línea después de un intento fallido de explotación.

Una vez que hayamos explotado con éxito un objetivo y tengamos acceso inicial (¡y hayamos tomado notas claras para nuestros informes y registrado todas las actividades en nuestro registro de actividades!), pasaremos a las etapas posteriores a la explotación y al movimiento lateral.