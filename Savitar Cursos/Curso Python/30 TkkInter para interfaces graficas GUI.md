**Tkinter: Explorando Componentes Clave**

Ejemplos en :
`/home/alexandross/Adrian/Estudio/Cursos Hack/Savitar Academy/Python/TkInterProjets`


**1. tk.Label**

- **Descripción**: ‘**tk.Label**‘ es un widget en Tkinter utilizado para mostrar texto o imágenes. El texto puede ser estático o actualizarse dinámicamente.
- **Uso Común**: Se usa para añadir etiquetas informativas en una GUI, como títulos, instrucciones o información de estado.
- **Características Clave**:
    - **text**: Para establecer el texto que se mostrará.
    - **font**: Para personalizar la tipografía.
    - **bg y fg**: Para establecer el color de fondo (bg) y de texto (fg).
    - **image**: Para mostrar una imagen.
    - **wraplength**: Para especificar a qué ancho el texto debería envolverse.

**2. mainloop()**

- **Descripción**: ‘**mainloop()**‘ es una función esencial en Tkinter que ejecuta el bucle de eventos de la aplicación. Este bucle espera eventos, como pulsaciones de teclas o clics del mouse, y los procesa.
- **Importancia**: Sin ‘**mainloop()**‘, la aplicación GUI no responderá a eventos y parecerá congelada. Es lo que mantiene viva la aplicación.

**3. pack()**

- **Descripción**: ‘**pack()**‘ es un método de geometría usado para colocar widgets en una ventana.
- **Funcionalidad**: Organiza los widgets en bloques antes de colocarlos en la ventana. Los widgets se “empaquetan” en el orden en que se llama a ‘**pack()**‘.
- **Características Clave**:
    - **side**: Para especificar el lado de la ventana donde se ubicará el widget (por ejemplo, top, bottom, left, right).
    - **fill**: Para determinar si el widget se expande para llenar el espacio disponible.
    - **expand**: Para permitir que el widget se expanda para ocupar cualquier espacio adicional en la ventana.

**4. grid()**

- **Descripción**: ‘**grid()**‘ es otro método de geometría utilizado en Tkinter para colocar widgets.
- **Funcionalidad**: Organiza los widgets en una cuadrícula. Se especifica la fila y la columna donde debe ir cada widget.
- **Características Clave**:
    - **row y column**: Para especificar la posición del widget en la cuadrícula.
    - **rowspan y columnspan**: Para permitir que un widget ocupe múltiples filas o columnas.
    - **sticky**: Para determinar cómo se alinea el widget dentro de su celda (por ejemplo, N, S, E, W).