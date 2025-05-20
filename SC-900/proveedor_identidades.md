# Rol del Proveedor de Identidades

## Autenticación Moderna
- Término genérico para los métodos de autenticación y autorización entre un cliente (portátil, teléfono) y un servidor (sitio web, aplicación).
- En el centro de la autenticación moderna está el rol del **proveedor de identidades**.

## Funciones del Proveedor de Identidades
- Crear, mantener y administrar la información de identidad.
- Proporcionar servicios de:
  - Autenticación.
  - Autorización.
  - Auditoría.

## Ventajas de un Proveedor de Identidades Central
- Almacena y administra de forma centralizada la información de identidad.
- Permite a las organizaciones:
  - Establecer directivas de autenticación y autorización.
  - Supervisar el comportamiento de los usuarios.
  - Identificar actividades sospechosas.
  - Reducir ataques malintencionados.

## Proceso de Autenticación Moderna
1. El cliente se comunica con el proveedor de identidades mediante la asignación de una identidad que se puede autenticar.
2. Una vez comprobada la identidad (usuario o aplicación), el proveedor de identidades emite un **token de seguridad**.
3. El cliente envía el token al servidor.
4. El servidor valida el token a través de su **relación de confianza** con el proveedor de identidades.
5. Usando el token y la información que contiene, el usuario o aplicación accede a los recursos necesarios en el servidor.

## Ejemplos de Proveedores de Identidades
- **Microsoft Entra ID** (basado en la nube).
- Google.
- Amazon.
- LinkedIn.
- GitHub.

## Inicio de Sesión Único (SSO)
- Funcionalidad clave de un proveedor de identidades y la autenticación moderna.
- Permite que el usuario inicie sesión una vez y use esa credencial para acceder a múltiples aplicaciones o recursos.
- Configurar el SSO entre varios proveedores de identidades se conoce como **federación**.
