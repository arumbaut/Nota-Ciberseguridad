# Modelo de Responsabilidad Compartida

## Introducción

En organizaciones que solo ejecutan hardware y software local, la organización es 100% responsable de la implementación de la seguridad y el cumplimiento. Con los servicios basados en la nube, esa responsabilidad se comparte entre el cliente y el proveedor de la nube.

## Centros de Datos Locales

- Seguridad física
- Administración completa de hardware y software
- Cifrado de información confidencial

## Infraestructura como Servicio (IaaS)

### Cliente gestiona:

- Sistemas operativos
- Controles de red
- Aplicaciones
- Protección de datos

### Proveedor gestiona:

- Equipos físicos
- Red
- Seguridad del centro de datos

### Herramientas y Metodologías:

- Firewalls
- Gestión de identidad y acceso (IAM)
- Seguridad en la nube

## Plataforma como Servicio (PaaS)

### Cliente gestiona:

- Aplicaciones
- Datos

### Proveedor gestiona:

- Hardware
- Sistemas operativos

### Herramientas y Metodologías:

- CI/CD (Integración y Despliegue Continuo)
- Contenedores (Docker, Kubernetes)
- Seguridad en el desarrollo (DevSecOps)

## Software como Servicio (SaaS)

### Proveedor gestiona:

- Hospedaje y mantenimiento del software

### Cliente gestiona:

- Datos
- Dispositivos
- Cuentas e identidades

### Ejemplos:

- Microsoft 365
- Skype
- Dynamics CRM Online

### Herramientas y Metodologías:

- Gestión de acceso y control (MFA, SSO)
- Cifrado de datos
- Auditorías de seguridad

## Responsabilidades del Cliente

- Gestión de la información y datos
- Seguridad de dispositivos (móviles y equipos)
- Administración de cuentas e identidades

## Ventajas del Modelo

- Claridad en las responsabilidades compartidas
- Seguridad mejor distribuida entre cliente y proveedor
- Reducción de carga de gestión para el cliente
- Enfoque en desarrollo sin preocuparse por infraestructura

---

# Defensa en Profundidad

## Introducción

La defensa en profundidad usa un enfoque por capas para la seguridad, en lugar de depender de un solo perímetro. Una estrategia de defensa en profundidad usa una serie de mecanismos para ralentizar el avance de un ataque. Cada capa proporciona protección de modo que, si se infringe una de ellas, una capa posterior impedirá que un atacante obtenga acceso no autorizado a los datos.

## Niveles de Seguridad

### Seguridad Física
- Control de acceso a centros de datos solo para personal autorizado.

### Identidad y Acceso
- Autenticación multifactor (MFA).
- Acceso basado en condiciones.
- Control de cambios en la infraestructura.

### Seguridad Perimetral de la Red
- Protección contra ataques DDoS.
- Filtrado de ataques antes de afectar el servicio.

### Seguridad de Red
- Segmentación de red.
- Controles de acceso a la red.
- Restricción de comunicación entre recursos.

### Seguridad de Proceso
- Protección del acceso a máquinas virtuales.
- Cierre de puertos innecesarios.

### Seguridad de Aplicación
- Desarrollo de aplicaciones seguras.
- Eliminación de vulnerabilidades de seguridad.

### Seguridad de Datos
- Control de acceso a datos empresariales y de clientes.
- Cifrado de datos para mayor protección.

## Beneficios de la Defensa en Profundidad

- Reducción del riesgo de accesos no autorizados.
- Protección contra múltiples vectores de ataque.
- Mayor tiempo de respuesta ante incidentes.
- Cumplimiento de regulaciones y estándares de seguridad.
