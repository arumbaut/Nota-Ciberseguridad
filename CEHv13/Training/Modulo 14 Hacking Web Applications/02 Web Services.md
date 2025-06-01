Un servicio web es una aplicación o software que se implementa a través de Internet. Utiliza un protocolo de mensajería estándar (como **SOAP**) para permitir la comunicación entre aplicaciones desarrolladas en diferentes plataformas. Por ejemplo, servicios desarrollados en **Java** pueden interactuar con aplicaciones desarrolladas en **PHP**.

² **SOAP** (Simple Object Access Protocol): Un protocolo basado en XML que permite el intercambio de información estructurada entre aplicaciones.

² **UDDI** (Universal Description, Discovery, and Integration): Un directorio que permite a las aplicaciones encontrar y conectarse con servicios web.

² **WSDL** (Web Services Description Language): Un lenguaje basado en XML que describe los servicios web disponibles y cómo acceder a ellos.

² **REST** (Representational State Transfer): Un enfoque arquitectónico ligero que utiliza HTTP y es ampliamente utilizado por servicios web modernos debido a su simplicidad y eficiencia.

² **WS-Security** (Web Services Security):  
Es una extensión del protocolo SOAP que proporciona mecanismos de seguridad para los servicios web. Su objetivo es garantizar la integridad, confidencialidad y autenticación de los mensajes SOAP mediante el uso de firmas digitales, cifrado y tokens de seguridad.

#### **Web Service Architecture**

La arquitectura de un servicio web describe las interacciones entre tres entidades clave:

**Proveedor del servicio (Service Provider)**

**Solicitante del servicio (Service Requester)**

**Registro del servicio (Service Registry)**

Estas entidades interactúan a través de tres operaciones principales:

**Publicar (Publish):**  
El proveedor del servicio desarrolla e implementa un servicio web y publica su descripción (usualmente en WSDL) en el registro de servicios (UDDI, por ejemplo).

**Buscar (Find):**  
El solicitante del servicio consulta el registro para encontrar la descripción del servicio que necesita.

**Vincular (Bind):**  
Usando la información obtenida del registro, el solicitante establece una conexión con el proveedor del servicio para invocar su funcionalidad.

Estas interacciones giran en torno a artefactos del servicio web, es decir, módulos de software (servicios) y sus respectivas descripciones. La arquitectura asegura que los servicios puedan ser descubiertos, accedidos y utilizados de manera estándar y eficiente a través de diferentes plataformas y lenguajes de programación.

#### **Types of Web Services**

**▪ SOAP web services**: 
Define el formato XML. XML se utiliza para transferir datos entre el proveedor del servicio y el solicitante. También determina el procedimiento para construir servicios web y permite el intercambio de datos entre diferentes lenguajes de programación.

**▪ RESTful web services**:
REpresentational State Transfer (RESTful) web services están diseñados para hacer los servicios más productivos. Utilizan muchos conceptos subyacentes de HTTP para definir los servicios. Es un enfoque arquitectónico en lugar de un protocolo como SOAP.

**Componentes de la arquitectura de servicios web:**  
**▪ UDDI:** Universal Description, Discovery, and Integration (UDDI) es un servicio de directorio que lista todos los servicios disponibles.  
**▪ WSDL:** Web Services Description Language es un lenguaje basado en XML que describe y traza servicios web.  
**▪ WS-Security:** Web Services Security (WS-Security) desempeña un papel importante en la protección de los servicios web. Es una extensión de SOAP y tiene como objetivo mantener la integridad y confidencialidad de los mensajes SOAP, así como autenticar a los usuarios.

#### **Web Application Threats**

##### **OWASP Top 10 Application Security Risks – 2021 Source: https://owasp.org**

**==▪ A01 – Broken Access Control (Directory Traversal o Hidden Field Manipulation)**==
==**▪ A02 – Cryptographic Failures(Cookie Snooping, RC4 NOMORE Attack, Same-Site Attack, Pass-the-Cookie Attack)**==
==**▪ A03 – Injection(SQL Injection o Command Injection, LDAP Injection, Cross-Site Scripting (XXS), Buffer Overflow)**==
==**▪ A04 – Insecure Design(Business Logic Bypass Attack, Web-based Timing Attacks, CAPTCHA Attacks, Platform Exploits)**==
==**▪ A05 – Security Misconfiguration(XML External Entity (XXE) Attack, Unvalidated Redirects and Forwards)**==
==**▪ A06 – Vulnerable and Outdated Components(Platform Exploits, Magecart Attack, Buffer Overflow)**==
==**▪ A07 – Identification and Authentication Failures**==
==**▪ A08 – Software and Data Integrity Failures(Insecure Deserialization, Unvalidated Redirects and Forwards, Watering Hole Attack, Denial-of-Service (DoS), Buffer Overflow, Web Service Attacks, Platform Exploits, Magecart Attack)**==
==**▪ A09 – Security Logging and Monitoring Failures(Web Service Attacks)**==
==**▪ A10 – Server-Side Request Forgery (SSRF) (Injecting an SSRF Payload, Cross-Site Port Attack (XSPA), DNS Rebinding Attack, H2C Smuggling Attack)==**