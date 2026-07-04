# Servicios de Directorio, Active Directory y Federación

## Active Directory (AD)
- Conjunto de servicios de directorio desarrollados por Microsoft como parte de Windows 2000 para redes locales basadas en dominio.
- **Active Directory Domain Services (AD DS)**:
  - Servicio más conocido de Active Directory.
  - Almacena información sobre los miembros del dominio (dispositivos y usuarios).
  - Comprueba credenciales y define derechos de acceso.
  - Un servidor que ejecuta AD DS es un **controlador de dominio**.

## Importancia de AD DS
- Componente central de las organizaciones con infraestructura de TI local.
- Permite administrar varios sistemas y componentes de la infraestructura local mediante una única identidad por usuario.
- Limitaciones:
  - No es compatible de forma nativa con:
    - Dispositivos móviles.
    - Aplicaciones SaaS.
    - Aplicaciones de línea de negocio que requieren métodos de autenticación moderna.

## Microsoft Entra ID
- Anteriormente conocido como Azure Active Directory.
- Parte de la familia de soluciones de administración de identidades multinube denominada **Microsoft Entra**.
- Proporciona una solución de **Identidad como servicio (IDaaS)** para aplicaciones en la nube y locales.

## Federación

### Definición
- Permite el acceso a servicios a través de los límites de la organización o del dominio mediante relaciones de confianza entre proveedores de identidades (IdP).
- Beneficio: No es necesario que un usuario mantenga un nombre de usuario y contraseña diferentes al acceder a recursos de otros dominios.

### Relación de Confianza
- La confianza no siempre es bidireccional:
  - Ejemplo: IdP-A puede confiar en IdP-B y permitir que un usuario del dominio B acceda al sitio web del dominio A.
  - Lo contrario no es cierto a menos que se configure explícitamente la relación de confianza.

### Ejemplo Práctico
- Un usuario inicia sesión en un sitio de terceros con su cuenta de redes sociales (como X).
- En este caso:
  - **X** es un proveedor de identidades.
  - El sitio de terceros podría usar un proveedor de identidades diferente, como **Microsoft Entra ID**.
  - Existe una relación de confianza entre Microsoft Entra ID y X.
