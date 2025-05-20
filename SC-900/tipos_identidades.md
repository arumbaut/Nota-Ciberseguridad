# Tipos de Identidades

## Categorías de Identidades

### Identidades de Usuario
- Representan a personas como empleados y usuarios externos (clientes, consultores, proveedores y asociados).
- Características:
  - **Autenticación interna**: El usuario tiene una cuenta en Microsoft Entra ID de la organización de host.
  - **Autenticación externa**: El usuario se autentica mediante una cuenta de Microsoft Entra externa, una identidad de red social u otro proveedor de identidades externo.
- Tipos de usuarios:
  - **Miembro interno**: Empleados de la organización con autenticación interna.
  - **Invitado externo**: Consultores, proveedores y asociados con autenticación externa y permisos limitados.
  - **Miembro externo**: Usuarios de otros inquilinos con acceso de nivel de miembro.
  - **Invitado interno**: Usuarios configurados como invitados con permisos reducidos (escenario heredado).

### Identidades de Cargas de Trabajo
- Asignadas a cargas de trabajo de software para autenticar y acceder a servicios y recursos.
- **Aplicaciones y Entidades de Servicio**:
  - Una entidad de servicio es una identidad para una aplicación registrada en Microsoft Entra ID.
  - Permite autenticación y autorización de aplicaciones en recursos protegidos.
- **Identidades Administradas**:
  - Eliminan la necesidad de que los desarrolladores administren credenciales.
  - Tipos:
    - **Asignadas por el sistema**: Asociadas al ciclo de vida de un recurso de Azure.
    - **Asignadas por el usuario**: Independientes de los recursos y pueden asignarse a múltiples instancias.

### Identidades de Dispositivo
- Asignadas a productos de hardware como dispositivos móviles, portátiles, servidores e impresoras.
- Tipos de dispositivos en Microsoft Entra ID:
  - **Dispositivos registrados**: Compatibles con escenarios BYOD (Bring Your Own Device).
  - **Dispositivos unidos a Microsoft Entra**: Propiedad de la organización y unidos a Microsoft Entra ID.
  - **Dispositivos unidos a Microsoft Entra híbrido**: Unidos a Active Directory local y Microsoft Entra ID.
- Beneficios:
  - Inicio de sesión único (SSO) a recursos en la nube y locales.

### Grupos
- Permiten agrupar identidades con las mismas necesidades de acceso.
- Tipos de grupos:
  - **Grupos de Seguridad**: Administran el acceso de usuarios y dispositivos a recursos compartidos.
  - **Grupos de Microsoft 365**: Diseñados para colaboración y no requieren rol de administrador para su creación.
- Principio de seguridad: Limitar el acceso solo a identidades que lo necesiten.
