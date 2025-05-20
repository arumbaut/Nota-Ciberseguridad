# Roles y Control de Acceso Basado en Roles (RBAC) de Microsoft Entra

## ¿Qué es RBAC de Microsoft Entra?
- La administración del acceso mediante roles se conoce como **Control de Acceso Basado en Roles (RBAC)**.
- Los roles de Microsoft Entra controlan el acceso a los recursos de Microsoft Entra.

---

## Roles Integrados
- Microsoft Entra ID incluye roles integrados con un conjunto fijo de permisos.
- Ejemplos de roles integrados:
  - **Administrador global**: Acceso a todas las características administrativas de Microsoft Entra.
  - **Administrador de usuarios**: Puede crear y administrar usuarios, grupos, incidencias de soporte y supervisar el estado del servicio.
  - **Administrador de facturación**: Realiza compras, administra suscripciones e incidencias de soporte.
- Los permisos de los roles integrados no se pueden modificar.

---

## Roles Personalizados
- Proporcionan flexibilidad para conceder acceso.
- **Definición de rol personalizado**:
  - Colección de permisos seleccionados de una lista preestablecida.
  - Los permisos disponibles son los mismos que los de los roles integrados.
- **Asignación de roles**:
  - Concede permisos de un rol personalizado en un ámbito específico (toda la organización o un objeto específico).
  - Ejemplo: Un usuario puede tener permisos en todas las aplicaciones o solo en una aplicación específica.
- Requieren una licencia de Microsoft Entra ID P1 o P2.

### Procedimiento Recomendado
- Conceder el privilegio mínimo necesario para realizar el trabajo.
- Ejemplo: Asignar el rol de administrador de usuarios en lugar de administrador global si solo se administran usuarios.

---

## Categorías de Roles de Microsoft Entra

### Roles Específicos de Microsoft Entra
- Permisos para administrar recursos solo en Microsoft Entra.
- Ejemplos: Administrador de usuarios, Administrador de aplicaciones, Administrador de grupos.

### Roles Específicos del Servicio
- Permisos para administrar características de servicios específicos de Microsoft 365.
- Ejemplos: Administrador de Exchange, Administrador de Intune, Administrador de SharePoint, Administrador de Teams.

### Roles Entre Servicios
- Permisos que abarcan varios servicios.
- Ejemplos:
  - **Administrador de seguridad**: Acceso a servicios de seguridad dentro de Microsoft 365.
  - **Administrador de cumplimiento**: Acceso a configuraciones relacionadas con el cumplimiento en el Centro de cumplimiento de Microsoft 365, Exchange, etc.

---

## Diferencias entre RBAC de Microsoft Entra y RBAC de Azure

### RBAC de Microsoft Entra
- Controla el acceso a recursos de Microsoft Entra como usuarios, grupos y aplicaciones.

### RBAC de Azure
- Controla el acceso a recursos de Azure como máquinas virtuales o almacenamiento.

### Diferencias Clave
- **Almacenes de datos**: Las definiciones y asignaciones de roles se almacenan en diferentes ubicaciones.
- **Puntos de decisión de directivas**: Las comprobaciones de acceso se realizan en diferentes puntos.
