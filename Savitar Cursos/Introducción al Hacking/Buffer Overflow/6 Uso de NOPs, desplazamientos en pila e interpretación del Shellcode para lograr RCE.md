- Tags : #buffer_overflow 

Una vez que se ha encontrado la dirección del opcode que aplica el salto al registro **ESP**, es posible que el shellcode no sea interpretado correctamente debido a que su ejecución puede requerir más tiempo del que el procesador tiene disponible antes de continuar con la siguiente instrucción del programa.

Para solucionar este problema, se suelen utilizar técnicas como la introducción de **NOPS** (**instrucciones de no operación**) antes del shellcode en la pila. Los NOPS no realizan ninguna operación, pero permiten que el procesador tenga tiempo adicional para interpretar el shellcode antes de continuar con la siguiente instrucción del programa.

Otra técnica que se suele utilizar es el desplazamiento en la pila, que implica modificar el registro ESP para reservar espacio adicional para el shellcode y permitir que se ejecute sin problemas. Por ejemplo, se puede utilizar la instrucción “**sub esp, 0x10**” para desplazar el registro ESP **16 bytes** hacia abajo en la pila y reservar espacio adicional para el shellcode.

Ya con esto, ¡habríamos conseguido vulnerar el sistema a través del Buffer Overflow!

Hasta este punto tenemos el script pero no logramos que se ejecute la shell pues en muchas ocaciones se necesita mas tiempo de ejecución para la instrucción por lo que necesitamos ampliar el este tiempo en el programa
![](../../../attachments/Pasted%20image%2020260224224343.png)


![](../../../attachments/Pasted%20image%2020260224224714.png)
Nos ponemos a la escuche 
```bash
rlwrap nc -nlvp 4646
```

Ejecutamos el script de python ya estructurado anteriormente con las nuevas modificaciones y obtenemos una **cmd** de windows