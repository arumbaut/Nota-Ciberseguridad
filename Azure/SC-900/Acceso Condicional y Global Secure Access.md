# Acceso Condicional y Global Secure Access

## Acceso Condicional

### Definición
- Característica de Microsoft Entra ID que proporciona una capa de seguridad adicional antes de permitir el acceso a datos o recursos.
- Implementado a través de directivas que analizan señales como usuario, ubicación, dispositivo, aplicación y riesgo.
- Ejemplo: Si un usuario pertenece a un grupo específico, se le solicita autenticación multifactor para acceder a una aplicación.

### Componentes de una Directiva de Acceso Condicional

#### Asignaciones
- Controlan el **quién**, el **qué**, el **dónde** y el **cuándo** de una directiva.
- Todas las asignaciones deben cumplirse (operación lógica AND).
- Tipos de asignaciones:
  - **Usuarios**: Incluye o excluye usuarios, grupos, roles, invitados externos e identidades de carga de trabajo.
  - **Recursos de destino**: Aplicaciones, servicios, acciones de usuario, Global Secure Access o contexto de autenticación.
  - **Cloud Apps**: Aplicaciones integradas de Microsoft, Office 365, portales de administración y aplicaciones registradas.
  - **Acciones del usuario**: Registrar información de seguridad, unirse a dispositivos, etc.
  - **Network**: Controla el acceso según la red o ubicación física del usuario.
  - **Condiciones**: Incluyen riesgo de inicio de sesión, riesgo del usuario, plataforma de dispositivos, aplicaciones cliente y filtros para dispositivos.

#### Controles de Acceso
- Deciden cómo se aplica una directiva:
  - **Bloquear acceso**.
  - **Conceder acceso**: Puede incluir controles adicionales como autenticación multifactor, dispositivos compatibles, cambio de contraseña, etc.
  - **Sesión**: Experiencias limitadas en aplicaciones específicas (por ejemplo, bloquear descargas o copiar documentos confidenciales).

---

## Microsoft Global Secure Access

### Definición
- Conjunto de productos que incluye **Microsoft Entra Internet Access** y **Microsoft Entra Private Access**.
- Proporciona controles de acceso de red, identidad y punto de conexión bajo el modelo de Confianza Cero.

### Componentes

#### Acceso a Internet de Microsoft Entra
- Solución de puerta de enlace web segura (SWG) para proteger aplicaciones SaaS y tráfico de Internet.
- Características clave:
  - Protección contra robo de identidad o tokens.
  - Cumplimiento en el plano de autenticación y datos.
  - Evaluación continua del acceso (CAE).
  - Restricciones de inquilinos para evitar filtraciones de datos.
  - Filtrado de contenido web.

#### Acceso Privado de Microsoft Entra
- Reemplaza las VPN heredadas para acceso seguro a recursos privados corporativos.
- Métodos de configuración:
  - **Acceso rápido**: Define recursos privados mediante FQDN, IP o puertos.
  - **Aplicación de Acceso Seguro Global**: Configuración granular para diferentes recursos y directivas.

---

## Panel de Global Secure Access
- Proporciona visualizaciones del tráfico de red adquirido por los servicios de Acceso Privado e Internet de Microsoft Entra.
- Widgets disponibles:
  - **Instantánea de Acceso Seguro Global**: Resumen de usuarios, dispositivos y aplicaciones protegidas.
  - **Alertas y Notificaciones**: Identifica actividades sospechosas o tendencias.
  - **Acceso entre inquilinos**: Visibilidad sobre usuarios y dispositivos que acceden a otros inquilinos.
  - **Filtrado de Categorías Web**: Muestra categorías de contenido bloqueado o permitido.
  - **Estado del Dispositivo**: Dispositivos activos e inactivos implementados.
