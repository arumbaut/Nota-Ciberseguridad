# Métodos de Autenticación

## Métodos de Autenticación en Microsoft Entra ID

### Contraseñas
- Forma más común de autenticación.
- Problemas:
  - Vulnerables si se usan como único factor de autenticación.
  - Fáciles de recordar, pero también fáciles de vulnerar.
- Recomendación: Complementar o reemplazar con métodos más seguros.

### Teléfono
- **Autenticación basada en SMS**:
  - El usuario ingresa su número de teléfono móvil registrado.
  - Recibe un código de verificación por SMS y lo ingresa para iniciar sesión.
- **Comprobación por llamada de voz**:
  - Llamada automatizada al número registrado.
  - El usuario presiona # para completar el inicio de sesión.
  - Solo se admite como forma secundaria de autenticación.

### JURAMENTO (OATH)
- Estándar abierto para generar códigos de contraseña de un solo uso (TOTP).
- **Tokens de software OATH**:
  - Aplicaciones que generan códigos OTP basados en una clave secreta.
- **Tokens de hardware OATH TOTP**:
  - Dispositivos físicos que generan códigos actualizados cada 30-60 segundos.
  - Solo se admiten como formas secundarias de autenticación.

### Autenticación sin Contraseñas
- Elimina el uso de contraseñas en eventos de inicio de sesión.
- Métodos:
  - **Windows Hello para Empresas**:
    - Autenticación de dos factores (clave/certificado + PIN o biometría).
    - Forma principal o secundaria de autenticación.
  - **FIDO2**:
    - Estándar abierto para autenticación sin contraseña.
    - Usa dispositivos USB, Bluetooth o NFC para autenticar.
    - Forma principal o secundaria de autenticación.
  - **Microsoft Authenticator**:
    - Convierte un teléfono en una credencial segura sin contraseña.
    - Disponible para Android e iOS.
  - **Autenticación basada en certificados (CBA)**:
    - Usa certificados X.509 para autenticar directamente.
    - Solo se admite como forma principal de autenticación.

---

## Autenticación Multifactor (MFA)
- Solicita una forma adicional de identificación durante el inicio de sesión.
- Factores de autenticación:
  - **Algo que sabe**: Contraseña o PIN.
  - **Algo que tiene**: Dispositivo de confianza (teléfono, clave de hardware).
  - **Algo que es**: Información biométrica (huella digital, detección de rostro).
- Beneficios:
  - Mejora drástica de la seguridad de las identidades.
  - Simple para los usuarios.

### Valores Predeterminados de Seguridad
- Conjunto de mecanismos básicos recomendados por Microsoft.
- Características:
  - Registro obligatorio de MFA para todos los usuarios.
  - MFA obligatorio para administradores.
  - MFA requerido para todos los usuarios cuando sea necesario.

---

## Autoservicio de Restablecimiento de Contraseña (SSPR)
- Permite a los usuarios cambiar o restablecer su contraseña sin intervención del administrador.
- Ventajas:
  - Reduce costos de soporte técnico.
  - Aumenta la productividad de los usuarios.
  - Configuración adaptable a nuevos requisitos de seguridad.
  - Registros de auditoría disponibles para integración con sistemas SIEM.
- Requisitos:
  - Licencia de Microsoft Entra ID asignada.
  - Habilitación para SSPR por un administrador.
  - Registro con métodos de autenticación (se recomiendan al menos dos).
- Métodos de autenticación disponibles:
  - Notificación en aplicación móvil.
  - Código de aplicación móvil.
  - Correo electrónico.
  - Teléfono móvil.
  - Teléfono del trabajo.
  - Preguntas de seguridad.
- **Reescritura de Contraseñas**:
  - Permite usar credenciales actualizadas con aplicaciones y dispositivos locales.
