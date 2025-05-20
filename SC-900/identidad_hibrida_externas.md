# Identidad Híbrida e Identidades Externas

## Identidad Híbrida

### Definición
- Las soluciones de identidad de Microsoft abarcan funcionalidades locales y basadas en la nube.
- Crean una identidad común para la autenticación y autorización en todos los recursos, independientemente de la ubicación.

### Métodos para Lograr Identidad Híbrida

#### Aprovisionamiento
- Aprovisiona una identidad entre dos sistemas de servicios de directorio diferentes.
- Escenario común: Un usuario en Active Directory se aprovisiona en Microsoft Entra ID.

#### Sincronización
- Garantiza que la información de identidad de los usuarios y grupos locales coincida con la de la nube.

### Microsoft Entra Cloud Sync
- Diseñado para cumplir objetivos de identidad híbrida mediante aprovisionamiento y sincronización de usuarios, grupos y contactos con Microsoft Entra ID.
- Usa el **agente de aprovisionamiento en la nube de Microsoft Entra**:
  - Actúa como puente entre Microsoft Entra ID y Active Directory.
  - Configuración de aprovisionamiento almacenada en Microsoft Entra ID.
- Basado en la especificación **System for Cross-domain Identity Management (SCIM)**:
  - Estándar para automatizar el intercambio de información de identidad entre dominios.

---

## Identidades Externas

### Definición
- Soluciones para trabajar con personas externas a la organización.
- Permiten que identidades externas accedan de forma segura a aplicaciones y recursos.
- Ejemplos de identidades externas:
  - Cuentas corporativas.
  - Identidades emitidas por el gobierno.
  - Proveedores de identidades de redes sociales (Google, Facebook).

### Escenarios de Identidades Externas

#### Colaboración con Invitados Empresariales
- Usa **Id. externa** para la colaboración B2B:
  - Permite a los empleados colaborar con socios comerciales externos.
  - Acceso a aplicaciones como:
    - Office 365.
    - Aplicaciones SaaS.
    - Aplicaciones de línea de negocio.

#### Protección de Aplicaciones para Consumidores y Clientes Empresariales
- Usa **Id. externa** para agregar autenticación y administración de identidades y acceso de clientes (CIAM) a aplicaciones.
- Funcionalidades de CIAM:
  - Registro de autoservicio.
  - Experiencias de inicio de sesión personalizadas (SSO con identidades sociales y empresariales).
  - Administración de cuentas de cliente.
- Beneficios:
  - Seguridad mejorada.
  - Cumplimiento.
  - Escalabilidad.

### Configuración de Inquilinos
- **Inquilino de Personal**:
  - Para empleados, aplicaciones empresariales internas y recursos organizativos.
  - Permite invitar a asociados empresariales externos.
- **Inquilino Externo**:
  - Exclusivo para escenarios de Id. externa.
  - Publicación de aplicaciones para consumidores o clientes empresariales.
