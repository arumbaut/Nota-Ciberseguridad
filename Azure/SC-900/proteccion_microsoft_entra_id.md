# Protección de Microsoft Entra ID

## ¿Qué es la Protección de Microsoft Entra ID?
- Ayuda a las organizaciones a detectar, investigar y corregir riesgos relacionados con identidades de usuario y de carga de trabajo.
- Los riesgos detectados pueden integrarse con herramientas como Acceso Condicional o sistemas SIEM para investigaciones más detalladas.

---

## Detección de Riesgos
- Microsoft analiza **billones de señales al día** para identificar posibles amenazas.
- Fuentes de señales: Microsoft Entra ID, cuentas de Microsoft, Xbox, entre otras.

### Tipos de Riesgos Detectados
1. **Riesgo de Inicio de Sesión:**
   - Probabilidad de que un inicio de sesión no esté autorizado por el propietario de la identidad.
   - Ejemplos:
     - Inicio de sesión desde una IP anónima.
     - Viaje inusual (ubicaciones geográficamente distantes).
     - Propiedades de inicio de sesión desconocidas.

2. **Riesgo de Usuario:**
   - Probabilidad de que una identidad o cuenta esté comprometida.
   - Ejemplos:
     - Credenciales filtradas.
     - Actividad sospechosa reportada por el usuario.
     - Patrones de envío sospechosos.

### Acciones Desencadenadas
- Solicitar autenticación multifactor (MFA).
- Requerir un restablecimiento de contraseña.
- Bloquear el acceso hasta que un administrador intervenga.

---

## Investigación de Riesgos
- Los riesgos detectados se rastrean mediante **informes clave**:
  1. **Detecciones de Riesgo:** Cada riesgo detectado se notifica como una detección.
  2. **Inicios de Sesión de Riesgo:** Se notifican cuando hay una o más detecciones de riesgo asociadas al inicio de sesión.
  3. **Usuarios de Riesgo:**
     - Un usuario tiene uno o más inicios de sesión de riesgo.
     - Se notifican una o más detecciones de riesgo.

### Funcionalidades Avanzadas
- **Microsoft Security Copilot:**
  - Resumen del nivel de riesgo de un usuario.
  - Información relevante del incidente.
  - Recomendaciones para mitigación rápida.

---

## Corrección de Riesgos
- **Corrección Automática:**
  - Directivas de acceso condicional basadas en riesgos pueden requerir:
    - Autenticación segura.
    - Autenticación multifactor (MFA).
    - Restablecimiento de contraseña seguro.
  - Si el usuario cumple con el control de acceso, el riesgo se corrige automáticamente.

- **Corrección Manual:**
  - Los administradores revisan riesgos manualmente en:
    - Informes del portal.
    - API de Microsoft Graph.
    - Microsoft Defender XDR.
  - Acciones manuales:
    - Descartar riesgos.
    - Confirmar seguridad.
    - Confirmar riesgo.

---

## Exportación de Datos
- Los datos de Identity Protection pueden exportarse para:
  - Archivo.
  - Investigación posterior.
  - Correlación en herramientas como SIEM.
- Métodos de exportación:
  - API de Microsoft Graph.
  - Área de trabajo de Log Analytics.
  - Cuentas de almacenamiento.
  - Event Hubs.
