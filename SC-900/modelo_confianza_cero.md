# Descripción del modelo de Confianza Cero

El modelo de **confianza cero** presupone que todo está en una red abierta y que no es de confianza, incluso los recursos detrás de los firewalls de la red corporativa. Este modelo funciona con el principio de **"no confiar en nadie y comprobarlo todo"**.

Ya no asumimos que una contraseña es suficiente para validar a un usuario, sino que agregamos la **autenticación multifactor** para proporcionar comprobaciones adicionales. En lugar de conceder acceso a todos los dispositivos de la red corporativa, solo se permite el acceso de los usuarios a las aplicaciones o a los datos específicos que necesiten.

---

## Principios de GUID de Confianza Cero

El modelo de confianza cero tiene tres principios que guían y respaldan el modo de implementar la seguridad:

1. **Comprobación de forma explícita**  
   Autentique y autorice siempre el contenido en función de los puntos de datos disponibles, como:
   - La identidad del usuario.
   - La ubicación.
   - El dispositivo.
   - El servicio o la carga de trabajo.
   - La clasificación de los datos.
   - Las anomalías.

2. **Acceso con privilegios mínimos**  
   Limite el acceso de los usuarios mediante:
   - Acceso Just-in-Time (JIT) y Just-Enough Access (JEA).
   - Directivas de adaptación basadas en riesgos.
   - Protección de datos para garantizar la seguridad y la productividad.

3. **Asunción de infracciones de seguridad**  
   - Acceda al segmento mediante la red, el usuario, los dispositivos y la aplicación.
   - Use el cifrado para proteger los datos.
   - Utilice el análisis para obtener visibilidad, detectar amenazas y mejorar la seguridad.

---

## Seis pilares básicos

El modelo de confianza cero se basa en seis pilares fundamentales:

### 1. Identidades
Las **identidades** pueden ser usuarios, servicios o dispositivos. Cuando una identidad intenta obtener acceso a un recurso, debe:
- Comprobarse mediante la autenticación sólida.
- Seguir los principios de acceso con privilegios mínimos.

### 2. Dispositivos
Los **dispositivos** crean una superficie de ataque de gran tamaño a medida que los datos fluyen desde los dispositivos hasta las cargas de trabajo locales y en la nube.  
La supervisión del estado y el cumplimiento de los dispositivos es un aspecto importante de la seguridad.

### 3. Aplicaciones
Las **aplicaciones** son la manera en que se consumen los datos. Este pilar incluye:
- La detección de todas las aplicaciones que se usan (a veces denominada **Shadow IT**).
- La administración de permisos y acceso.

### 4. Datos
Los **datos** deben:
- Clasificarse, etiquetarse y cifrarse en función de sus atributos.  
En última instancia, los esfuerzos de seguridad están relacionados con la protección de los datos y garantizar que permanezcan seguros cuando salen de los dispositivos, las aplicaciones, la infraestructura y las redes que controla la organización.

### 5. Infraestructura
La **infraestructura**, ya sea local o en la nube, representa un vector de amenazas. Para mejorar la seguridad, debe:
- Evaluar la versión, la configuración y el acceso JIT.
- Usar la telemetría para detectar ataques y anomalías.
- Bloquear o marcar automáticamente el comportamiento de riesgo y tomar medidas de protección.

### 6. Redes
Las **redes** deben:
- Segmentarse, incluida la microsegmentación en la red más profunda.
- Emplear la protección contra amenazas en tiempo real.
- Usar cifrado, supervisión y análisis de un extremo a otro.

---

## Resumen

El modelo de confianza cero redefine la seguridad al asumir que nada es de confianza por defecto. A través de sus principios y pilares básicos, proporciona un enfoque integral para proteger identidades, dispositivos, aplicaciones, datos, infraestructura y redes.

