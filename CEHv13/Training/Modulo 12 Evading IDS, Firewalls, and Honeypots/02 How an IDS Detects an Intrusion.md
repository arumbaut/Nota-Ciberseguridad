#### **▪ Signature Recognition**

Intenta identificar eventos que indican un abuso del sistema o de la red. ==**Esta técnica consiste en crear modelos de posibles intrusiones y luego comparar dichos modelos con los eventos entrantes para tomar una decisión de detección. Las firmas en los IDS se desarrollan bajo la premisa de que el modelo debe detectar un ataque sin interferir con el tráfico normal del sistema**==. Solo los ataques deben coincidir con el modelo; de lo contrario, podrían generarse falsas alarmas.La detección por firmas compara los paquetes de red entrantes o salientes con las firmas binarias de ataques conocidos, utilizando técnicas simples de coincidencia de patrones.permite detectar ataques conocidos. Sin embargo, existe la posibilidad de que otros paquetes inofensivos contengan firmas similares, lo que podría activar alertas falsas (falsos positivos)

#### **▪ Anomaly Detection**

==**También conocida como “not-use detection,”  difiere del reconocimiento por firma. Este método se basa en una base de datos de anomalías. Se considera que hay una intrusión cuando un evento ocurre fuera del umbral de tolerancia del tráfico normal**==. Por lo tanto, cualquier desviación del uso regular se interpreta como un ataque.Este tipo de detección se basa en las características de comportamiento fijas de los usuarios y componentes de un sistema informático.

#### **▪ Protocol Anomaly Detection**

Consiste en analizar el tráfico de red para identificar desviaciones respecto a los estándares establecidos de los protocolos o patrones esperados de comportamiento. Este enfoque parte del supuesto de que la mayoría de los protocolos de red tienen reglas definidas, estructuras y comportamientos esperados. Cuando el tráfico no se ajusta a estas normas, puede ser señal de actividad maliciosa o errores de configuración.

**Funcionamiento de un detector de anomalías en protocolos:**

Comportamiento de referencia, Identificación de anomalías, Reglas de detección