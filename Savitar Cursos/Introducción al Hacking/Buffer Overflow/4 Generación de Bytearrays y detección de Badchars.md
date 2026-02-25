- Tags : #buffer_overflow 

En la generación de nuestro shellcode malicioso para la explotación del buffer overflow, es posible que algunos caracteres no sean interpretados correctamente por el programa objetivo. Estos caracteres se conocen como “**badchars**” y pueden causar que el shellcode falle o que el programa objetivo se cierre inesperadamente.

Para evitar esto, es importante identificar y eliminar los badchars del shellcode. En esta clase, veremos cómo desde Immunity Debugger podremos aprovechar la funcionalidad **Mona** para generar diferentes bytearrays con casi todos los caracteres representados, y luego identificar los caracteres que el programa objetivo no logra interpretar.

Una vez identificados los badchars, se pueden descartar del shellcode final y generar un nuevo shellcode que no contenga estos caracteres. Para identificar los badchars, se pueden utilizar diferentes técnicas, como la introducción de diferentes bytearrays con caracteres hexadecimales consecutivos, que permiten identificar los caracteres que el programa objetivo no logra interpretar.

Estos caracteres irán representados en la pila (**ESP**), que será donde veremos qué caracteres son los que no están siendo representados, identificando así los badchars.

Definimos nuestro directorio de trabajo con **MONA**

![](../../../attachments/Pasted%20image%2020260224181750.png)

![](../../../attachments/Pasted%20image%2020260224181912.png)
```
!mona config -set workingfolder C:\User\savitar\Desktop\Analysis
```

![](../../../attachments/Pasted%20image%2020260224182111.png)
```
!mona bytearray
```

Para un shellcode el null byte siempre genera problemas asi que es recomendable no contemplarlo que cuando se genera el bytearray lo podemos excluir 

```
!mona bytearray -cpb '\x00'
```

Nos interesa el archivo *bytearray* que nos genera en la carpeta que le indicamos a mona como *workingfolder* 
![](../../../attachments/Pasted%20image%2020260224190606.png)

Ejecutamos el script, vemos que como en ocasiones anteriores se detuvo el programa en Immunyti y le damos a fallowing dump en el registro ESP para revisar cuales son los caracteres que no detecto

![](../../../attachments/Pasted%20image%2020260224191038.png)

Se puede identificar de manera manual o con mona
![](../../../attachments/Pasted%20image%2020260224191345.png)

```
!mona compare -a ESP_VALUE -f archibo_bytearray.bin
!mona compare -a 022EA12B -f C:\Users\savitar\Desktop\Analysis\bitearray.bin

```

![](../../../attachments/Pasted%20image%2020260224191610.png)

Modificamos el payload de nuestro script eliminando el carácter que nos detecto y o volvemos a ejecutar y así sucesivamente hasta que el programa reconozca todos los caracteres que le pasamos. Es importante que luego de una comparación actualicemos el bytearray.bin excluyendo los caracteres que se han ido detectando como ilegibles
```
!mona bytearray -cpb '\x00\x0a\x0d' 
```

Y tambien ir actualizando el affter_eip en el script.

Esto lo haremos hasta que no obtengamos nada en el **BadChars**

![](../../../attachments/Pasted%20image%2020260224195059.png)