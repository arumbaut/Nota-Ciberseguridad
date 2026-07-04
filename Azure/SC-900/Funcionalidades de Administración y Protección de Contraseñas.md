# Funcionalidades de Administración y Protección de Contraseñas

## Protección de Contraseñas en Microsoft Entra ID
- Reduce el riesgo de que los usuarios establezcan contraseñas no seguras.
- Detecta y bloquea contraseñas no seguras conocidas y sus variantes.
- Permite bloquear términos poco seguros específicos para la organización.

### Listas de Contraseñas Prohibidas

#### Lista Global de Contraseñas Prohibidas
- Actualizada y aplicada automáticamente por Microsoft.
- Incluye contraseñas no seguras conocidas, como:
  - Ejemplo: P@$$w0rd, Passw0rd1 y sus variaciones.
- Mantenida por el equipo de protección de identidad de Microsoft Entra.
- Basada en datos de telemetría de seguridad para identificar contraseñas vulneradas.

#### Listas Personalizadas de Contraseñas Prohibidas
- Los administradores pueden crear listas personalizadas para necesidades específicas de seguridad empresarial.
- Ejemplos de términos que se pueden bloquear:
  - Nombres de marca.
  - Nombres de productos.
  - Ubicaciones (como la oficina central).
  - Términos internos específicos de la empresa.
  - Abreviaturas con significado específico en la organización.

### Protección contra la Difusión de Contraseñas
- Defiende contra ataques que intentan usar contraseñas menos seguras conocidas en múltiples cuentas.
- Bloquea eficazmente todas las contraseñas no seguras conocidas.
- Basada en datos de telemetría de seguridad del mundo real generados por Microsoft Entra.

### Seguridad Híbrida
- Permite integrar la protección de contraseñas de Microsoft Entra en entornos de Active Directory locales.
- Componentes:
  - Un componente local recibe la lista global de contraseñas prohibidas y las directivas personalizadas.
  - Los controladores de dominio procesan los eventos de cambio de contraseña.
- Beneficio: Garantiza que la protección de contraseñas de Microsoft Entra se aplique siempre que un usuario cambie su contraseña.
