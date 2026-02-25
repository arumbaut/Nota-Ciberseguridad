- Tags : #buffer_overflow 

Los **shellcodes** son programas pequeños y altamente optimizados que se utilizan para explotar vulnerabilidades de seguridad y ejecutar código malicioso en una máquina objetivo. Los shellcodes suelen ser escritos en lenguaje **ensamblador** para garantizar una ejecución rápida y eficiente.

En esta clase, exploraremos cómo funcionan los shellcodes por detrás mediante la creación de algunos shellcodes manualmente. Por ejemplo, intentaremos crear un shellcode que muestre por consola el mensaje “**Hola mundo**” utilizando interrupciones del sistema. Asimismo, intentaremos aplicar una llamada a nivel de sistema para lograr ejecutar un comando deseado.

Shellcode para linux, como paylos debemos elegir el que deseemos
```bash
msfvenom -p linux/x86/exec CMD="echo 'Hola Mundo'" -f elf -o shelcode
```