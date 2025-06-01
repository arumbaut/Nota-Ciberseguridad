### **▪ Verdadero Positivo (Ataque - Alerta)** **True Positive**

Ocurre cuando un evento activa una alarma y hace que el IDS reaccione como si un ataque real estuviera en progreso. El evento puede ser un ataque real, en cuyo caso un atacante intenta comprometer la red, o puede ser un simulacro, en cuyo caso el personal de seguridad usa herramientas de hacker para probar un segmento de la red.

### **▪ Falso Positivo (No hay ataque - Alerta)** **False Positive**

Ocurre cuando un evento activa una alarma, pero no hay un ataque real en progreso. Esto sucede cuando un IDS trata la actividad normal del sistema como si fuera un ataque.  Mientras prueban la configuración de un IDS, los administradores utilizan los falsos positivos para determinar si el IDS puede distinguir entre falsos positivos y ataques reales.

### **▪ Falso Negativo (Ataque - Sin Alerta)** **False Negative**

Ocurre cuando un IDS no reacciona ante un evento de ataque real. Esta condición es la falla más peligrosa, ya que el propósito de un IDS es detectar y responder a los ataques.

### **▪ Verdadero Negativo (No hay ataque - Sin Alerta)** **True Negative**

Condición que ocurre cuando un IDS identifica una actividad como comportamiento aceptable y la actividad resulta ser aceptable. Un verdadero negativo significa que se ha ignorado correctamente un comportamiento aceptable.