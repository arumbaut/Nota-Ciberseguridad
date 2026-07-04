---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/766"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Mantenerse organizado

---

Ya sea que estemos realizando evaluaciones de clientes, jugando CTF, tomando un curso en la Academia o en otro lugar, o jugando cajas/laboratorios HTB, la organización siempre es crucial. Es fundamental priorizar una documentación clara y precisa desde el principio. Esta habilidad nos beneficiará sin importar el camino que tomemos en seguridad de la información o incluso en otras trayectorias profesionales.

---

## Estructura de la carpeta

Al atacar una sola caja, laboratorio o entorno de cliente, debemos tener una estructura de carpetas clara en nuestra máquina de ataque para guardar datos como: información de alcance, datos de enumeración, evidencia de intentos de explotación, datos confidenciales como credenciales y otros datos obtenidos durante el reconocimiento, la explotación y la posexplotación. Una estructura de carpeta de muestra puede verse así:

```
shellsessionaalonso1190@htb[/htb]$ tree Projects/

Projects/
└── Acme Company
    ├── EPT
    │   ├── evidence
    │   │   ├── credentials
    │   │   ├── data
    │   │   └── screenshots
    │   ├── logs
    │   ├── scans
    │   ├── scope
    │   └── tools
    └── IPT
        ├── evidence
        │   ├── credentials
        │   ├── data
        │   └── screenshots
        ├── logs
        ├── scans
        ├── scope
        └── tools
```

Aquí tenemos una carpeta para el cliente `Acme Company` con dos evaluaciones, Prueba de Penetración Interna (IPT) y Prueba de Penetración Externa (EPT). Debajo de cada carpeta, tenemos subcarpetas para guardar datos de escaneo, cualquier herramienta relevante, salida de registro, información de alcance (es decir, listas de IP/redes para enviar a nuestras herramientas de escaneo) y una carpeta de evidencia que puede contener cualquier credencial recuperada durante la evaluación, cualquier dato relevante recuperado, así como capturas de pantalla.

Es una preferencia personal, pero algunas personas crean una carpeta para cada host de destino y guardan capturas de pantalla dentro de ella. Otros organizan sus notas por host o red y guardan capturas de pantalla directamente en la herramienta para tomar notas. Experimente con estructuras de carpetas y vea qué funciona mejor para usted para mantenerse organizado y trabajar de manera más eficiente.

---

## Herramientas para tomar notas

La productividad y la organización son muy importantes. Un probador de penetración muy técnico pero desorganizado tendrá dificultades para tener éxito en esta industria. Se pueden utilizar diversas herramientas para la organización y la toma de notas. Seleccionar una herramienta para tomar notas es algo muy individual. Es posible que algunos de nosotros no necesitemos una función que otra persona requiere según su flujo de trabajo. Algunas excelentes opciones para explorar incluyen:

|  |  |  |
| --- | --- | --- |
| [Cerezo](https://www.giuspen.com/cherrytree) | [Código de Visual Studio](https://code.visualstudio.com/) | [Evernote](https://evernote.com/) |
| [Noción](https://www.notion.so/) | [Libro Git](https://www.gitbook.com/) | [Texto sublime](https://www.sublimetext.com/) |
| [Bloc de notas++](https://notepad-plus-plus.org/downloads) |  |  |

Algunos de ellos se centran más en la toma de notas, mientras que otros, como Notion y GitBook, tienen funciones más completas que se pueden utilizar para crear páginas tipo Wiki, hojas de trucos y más. Es importante asegurarse de que todos los datos del cliente solo se almacenen localmente y no se sincronicen con la nube si se utiliza una de estas herramientas en evaluaciones del mundo real.

Consejo: Aprender [Markdown](https://en.wikipedia.org/wiki/Markdown) El lenguaje es fácil y muy útil para tomar notas, ya que se puede representar fácilmente de una manera visualmente atractiva y organizada.

---

## Otras herramientas y consejos

Todo profesional de seguridad de la información debe mantener una base de conocimientos. Esto puede ser en el formato que usted elija (aunque se recomiendan las herramientas anteriores) Esta base de conocimientos debe contener guías de referencia rápida para las tareas de configuración que realizamos en la mayoría de las evaluaciones y hojas de trucos para los comandos comunes que utilizamos para cada fase de una evaluación.

As we complete boxes, labs, assessments, training courses, etc., we should be aggregating every payload, command, tip as we never know when one may come in handy. Having them accessible will increase our overall efficiency and productivity. Each HTB Academy Module has a cheat sheet of relevant commands showcased within the Module sections, which you can download and keep for future reference.

We should also maintain checklists, report templates for various assessment types, and build a findings/vulnerability database. This database can take the form of a spreadsheet or something more complex and include a finding title, description, impact, remediation advice, and references. Having these findings already written will save us considerable time and re-work during the reporting phase as the bulk of the findings will be written already and likely only require some customization to the target environment.

---

## Moving On

Try out various note-taking tools and develop the folder structure that works for you and matches your methodology. Start early, so this becomes a habit! The Nibbles walkthrough later in this Module is an excellent opportunity to practice our documentation. Also, this Module contains many commands that are useful to add to our common commands cheat sheet.