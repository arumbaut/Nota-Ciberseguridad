##  **Tipos de Buffer Overflow**

---

###  **1. Stack-Based Buffer Overflow (Desbordamiento de Búfer en la Pila)**

 **Definición**:  
Un **stack-based buffer overflow** ocurre cuando se escriben más datos de los permitidos en un búfer ubicado en la **pila de memoria (stack)**.
Nota: Utiliza una pila estatica fija

 **Características clave**:

- La **pila (stack)** usa una estructura **LIFO** ("Último en entrar, primero en salir").
    
- Se utiliza para ** macenar variables locales** dentro de funciones.
    
- La memoria de la pila se **libera automáticamente** al finalizar la función.
    

 **Registros importantes**:

- **EBP** (Base Pointer): Marca el inicio del marco de pila.
    
- **ESP** (Stack Pointer): Señala la próxima posición libre.
    
- **EIP** (Instruction Pointer): Apunta a la **siguiente instrucción a ejecutar** (crítico en la explotación).
    
- **ESI / EDI**: Usados en operaciones con cadenas.
    

**Operaciones en la pila**:

- **PUSH**: Agrega datos a la pila.
    
- **POP**: Elimina datos de la pila.
    

 **Riesgo**:

- Si se sobrescribe **EIP**, se puede redirigir el flujo de ejecución del programa → **ejecución de código malicioso**.
    

---

### 🔷 **2. Heap-Based Buffer Overflow (Desbordamiento de Búfer en el Heap)**

📌 **Definición**:  
Un **heap-based buffer overflow** ocurre cuando se exceden los límites de un búfer ubicado en el **heap**, que es usado para la **asignación dinámica de memoria**. 
Nota: Utiliza la memoria dinamica

📌 **Características clave**:

- El **heap** se usa para **asignar memoria en tiempo de ejecución**.
    
- El programador debe gestionar la memoria manualmente con **malloc()** y **free()**.
    
- El acceso es **más lento** que en la pila.
    

📌 **Riesgos comunes**:

- Puede sobrescribir:
    
    - **Punteros a objetos**
        
    - **Encabezados del heap**
        
    - **Datos críticos o estructuras del programa**
        
    - **Tablas de funciones virtuales**
        

📌 **Dificultad**:

- La explotación en heap suele ser **menos predecible** y requiere técnicas más avanzadas.