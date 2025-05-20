# Privileged Identity Management (PIM)

## ¿Qué es PIM?
- Servicio de Microsoft Entra ID para administrar, controlar y supervisar el acceso a recursos importantes.
- Compatible con recursos de Microsoft Entra, Azure y otros servicios en línea como Microsoft 365 o Intune.
- **Objetivo:** Mitigar riesgos de permisos excesivos, innecesarios o mal utilizados.

### Características Principales
- **Just-in-Time:** Proporciona acceso con privilegios solo cuando es necesario.
- **Sujeto a plazos:** Asignación de fechas de inicio y fin para el acceso.
- **Basado en aprobación:** Requiere aprobación específica para activar privilegios.
- **Visible:** Envía notificaciones cuando se activan roles con privilegios.
- **Auditable:** Permite descargar un historial completo de acceso.

---

## ¿Por qué usar PIM?
- Reduce el número de personas con acceso a información o recursos seguros.
- Limita el tiempo de acceso para usuarios autorizados, minimizando riesgos.
- Supervisa las acciones realizadas por los usuarios con privilegios de administrador.

---

## Funcionalidades de PIM

### Roles Compatibles
- **Roles de Microsoft Entra:**
  - Roles integrados y personalizados para administrar Microsoft Entra ID y servicios de Microsoft 365.
- **Roles de Azure:**
  - Roles RBAC para grupos de administración, suscripciones, grupos de recursos y recursos.
- **PIM para Grupos:**
  - Pertenencia y propiedad Just-In-Time para grupos.
  - Compatible con Azure SQL, Azure Key Vault, Intune, roles de aplicaciones y aplicaciones de terceros.

### Flujo de Trabajo General
1. **Asignar:**
   - Asignación de roles a usuarios, grupos, entidades de servicio o identidades administradas.
   - **Datos de asignación:**
     - **Miembros o propietarios:** Quiénes tendrán el rol asignado.
     - **Ámbito:** Recursos específicos a los que se aplica el rol.
     - **Tipo de asignación:**
       - **Apto:** Requiere activación o aprobación para usar el rol.
       - **Activo:** No requiere acciones adicionales; privilegios asignados directamente.
     - **Duración:** Fechas de inicio y fin o asignación permanente.

2. **Activar:**
   - Los usuarios aptos deben activar el rol antes de usarlo.
   - Selección de duración de activación y motivo de la solicitud.

3. **Aprobar o Denegar:**
   - Los aprobadores reciben notificaciones por correo electrónico para gestionar solicitudes pendientes.
   - Una vez aprobada, el miembro puede usar el rol.

4. **Ampliar y Renovar:**
   - Solicitud de ampliación antes de la expiración del rol.
   - Solicitud de renovación tras la expiración del rol.

---

## Auditoría
- Historial de auditoría disponible para ver asignaciones y activaciones de roles de los últimos 30 días.
- Permite supervisar y rastrear el uso de roles con privilegios.
