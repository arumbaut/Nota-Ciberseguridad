# Microsoft Entra ID

## ¿Qué es Microsoft Entra ID?
- Anteriormente conocido como Active Directory.
- Servicio de administración de acceso e identidades basado en la nube de Microsoft.
- Usado por organizaciones para permitir que empleados, invitados y otros usuarios inicien sesión y accedan a recursos.

## Recursos que se pueden acceder con Microsoft Entra ID
- **Recursos internos**:
  - Aplicaciones de la red corporativa.
  - Intranet.
  - Aplicaciones en la nube desarrolladas por la organización.
- **Servicios externos**:
  - Microsoft Office 365.
  - Azure Portal.
  - Aplicaciones SaaS usadas por la organización.

## Beneficios
- Simplifica la administración de autorización y acceso.
- Proporciona un sistema de identidad único para aplicaciones locales y en la nube.
- Se puede sincronizar con:
  - Instancia de Active Directory local existente.
  - Otros servicios de directorio.
  - Usarse como un servicio independiente.

## Puntuación de Seguridad de la Identidad
- Indicador en porcentaje del grado de cumplimiento de las recomendaciones de seguridad de Microsoft.
- Cada acción de mejora se adapta a la configuración específica de la organización.

## Terminología Básica

### Inquilino
- Instancia de Microsoft Entra ID que contiene información sobre una sola organización.
- Incluye:
  - Usuarios.
  - Grupos.
  - Dispositivos.
  - Registros de aplicaciones.
- Contiene directivas de acceso y cumplimiento para recursos.
- Cada inquilino tiene:
  - Identificador único (id. de inquilino).
  - Nombre de dominio (por ejemplo, contoso.onmicrosoft.com).
- Actúa como límite de seguridad y administrativo.

### Directorio
- Contenedor lógico dentro de un inquilino de Microsoft Entra.
- Organiza recursos y objetos relacionados con la administración de identidades y acceso.
- Incluye:
  - Usuarios.
  - Grupos.
  - Aplicaciones.
  - Dispositivos.
- Un inquilino consta de un único directorio.

### Multiinquilino
- Organización con más de una instancia de Microsoft Entra ID.
- Razones para múltiples inquilinos:
  - Subsidiarias o unidades de negocio independientes.
  - Fusiones o adquisiciones.
  - Regulaciones geográficas.

## ¿Quién usa Microsoft Entra ID?

### Administradores de TI
- Controlan el acceso a recursos y aplicaciones corporativas según requisitos empresariales.
- Configuran autenticación multifactor para proteger recursos importantes.
- Proporcionan herramientas para:
  - Proteger identidades y credenciales de usuarios.
  - Cumplir requisitos de gobernanza de acceso.

### Desarrolladores
- Usan Microsoft Entra ID para agregar inicio de sesión único (SSO) a sus aplicaciones.
- Proporciona APIs para crear experiencias personalizadas con datos organizativos existentes.

## Acceso Automático
- Los suscriptores de servicios de Azure, Microsoft 365 o Dynamics 365 tienen acceso automático a Microsoft Entra ID.
- Pueden mejorar su implementación mediante licencias premium.
