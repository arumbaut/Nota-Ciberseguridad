# Gobernanza de Microsoft Entra ID

## ¿Qué es Microsoft Entra ID Governance?
- Permite equilibrar la productividad de los empleados y la seguridad organizacional.
- Garantiza que las personas adecuadas tengan el acceso adecuado a los recursos adecuados.
- Ofrece:
  - **Administración del ciclo de vida de las identidades.**
  - **Administración del ciclo de vida de los accesos.**
  - **Protección del acceso con privilegios.**

---

## Ciclo de Vida de las Identidades
- **Definición:** Proceso de administrar la identidad digital de los usuarios desde su creación hasta su eliminación.
- **Automatización:**
  - Aprovisionamiento entrante desde sistemas de RR. HH. (Workday, SuccessFactors).
  - Flujos de trabajo para eventos clave (inicio, cambios de estado, salida).
  - Directivas de asignación automática para roles y grupos.
  - Aprovisionamiento de usuarios en aplicaciones locales y en la nube.
- **Beneficio:** Garantiza que los usuarios tengan acceso actualizado y necesario para ser productivos.

---

## Ciclo de Vida de los Accesos
- **Definición:** Proceso para administrar el acceso de los usuarios durante su permanencia en la organización.
- **Automatización:**
  - Grupos dinámicos basados en atributos para pertenencia automática.
  - Administración de derechos para definir cómo los usuarios solicitan acceso.
  - Revisiones periódicas de acceso para recertificación.
- **Beneficio:** Escalabilidad y cumplimiento continuo de directivas de acceso.

---

## Ciclo de Vida de los Accesos con Privilegios
- **Definición:** Supervisión y control del acceso administrativo para minimizar riesgos.
- **Privileged Identity Management (PIM):**
  - Minimiza el número de personas con acceso administrativo.
  - Proporciona controles de gobernanza para proteger recursos.

---

## Revisiones de Acceso
- **Definición:** Permiten administrar pertenencias a grupos, acceso a aplicaciones y asignaciones de roles.
- **Casos de Uso:**
  - Reducir usuarios con privilegios excesivos.
  - Reconfirmar acceso a datos críticos.
  - Revisar excepciones a directivas.
  - Confirmar la necesidad de invitados en grupos.
- **Automatización:**
  - Revisiones periódicas (semanales, mensuales, trimestrales, anuales).
  - Cambios automáticos tras la revisión (quitar acceso, modificar permisos).
  - Revisiones de varias fases para flujos de trabajo complejos.

---

## Administración de Derechos
- **Definición:** Automatiza flujos de trabajo de solicitudes, asignaciones, revisiones y expiración de acceso.
- **Características:**
  - Delegación de creación de paquetes de acceso.
  - Administración de usuarios externos (invitación y eliminación automática).
  - Uso de paquetes de acceso para gestionar recursos.

---

## Términos de Uso de Microsoft Entra
- **Definición:** Presenta información a los usuarios antes de acceder a datos o aplicaciones.
- **Casos de Uso:**
  - Antes de acceder a datos confidenciales.
  - Recordatorios periódicos de regulaciones.
  - Términos específicos según roles o atributos del usuario.
- **Formato:**
  - Documento PDF creado por el usuario.
  - Compatible con dispositivos móviles.
- **Integración:**
  - Uso de directivas de acceso condicional para garantizar la aceptación de términos antes de acceder a recursos.
  - Los administradores pueden rastrear quién ha aceptado o rechazado los términos.
