#### **Honeypot**

Un honeypot es un sistema informático en Internet diseñado para atraer y atrapar a quienes intentan utilizar de manera no autorizada o ilícita el sistema anfitrión con el fin de penetrar la red de una organización. Es un proxy falso que se ejecuta para engañar a los atacantes, registrando el tráfico que pasa por él y luego enviando quejas a los proveedores de servicios de Internet (ISP) de las víctimas. No tiene ninguna actividad autorizada ni valor de producción, por lo que cualquier tráfico que reciba probablemente sea un sondeo, un ataque o una intrusión.

#### **Types of Honeypots**

**▪ Low-interaction Honeypots**

Emulan solo un número limitado de servicios y aplicaciones de un sistema o red objetivo. Si el atacante realiza una acción que la emulación no espera, el _honeypot_ simplemente generará un error. Capturan cantidades limitadas de información, es decir, principalmente datos transaccionales y algunas interacciones limitadas.

**▪ Medium-interaction Honeypots**

Simulan un sistema operativo real, así como aplicaciones y servicios de una red objetivo. Proporcionan un mayor nivel de engaño en comparación con los honeypots de baja interacción, lo que permite registrar y analizar ataques más complejos. Estos honeypots capturan datos más útiles y detallados, aunque solo pueden responder a comandos preconfigurados, lo que incrementa ligeramente el riesgo de intrusión.

**▪ High-Interaction Honeypots**

Los honeypots de alta interacción no emulan servicios ni sistemas, sino que ejecutan servicios y software reales con vulnerabilidades sobre sistemas operativos auténticos. Estos honeypots simulan por completo todos los servicios y aplicaciones de una red objetivo, y pueden ser totalmente comprometidos por los atacantes, lo que les da acceso completo al sistema —aunque en un entorno controlado.

**▪ Pure Honeypots**

Los honeypots puros emulan la red de producción real de una organización objetivo. Hacen que los atacantes dediquen su tiempo y recursos a atacar el sistema de producción crítico de la empresa. Los atacantes descubren y detectan las vulnerabilidades y activan alertas que ayudan a los administradores de red a proporcionar advertencias tempranas sobre ataques y, por lo tanto, reducir el riesgo de una intrusión.

**Honeypots are classified into the following types based on their deployment strategy**

**▪ Production Honeypots** :se implementan dentro de la red de producción de la organización junto con otros servidores de producción.

**▪ Research Honeypots** : son honeypots de alta interacción implementados principalmente por institutos de investigación, gobiernos u organizaciones militares para obtener conocimientos detallados sobre las acciones de los intrusos

**Honeypots are classified into the following types based on their deception technology**

**▪ Malware Honeypots :**
se utilizan para atrapar campañas de malware o intentos de malware a través de la infraestructura de red

**▪ Database Honeypots:**
emplean bases de datos falsas que son vulnerables a ataques relacionados con bases de datos, como inyecciones SQL y enumeración de bases de datos

**▪ Spam Honeypots** :
dirigidos específicamente a los spammers que abusan de recursos vulnerables como relays de correo abiertos y proxies abiertos.consisten en servidores de correo que aceptan deliberadamente correos electrónicos de cualquier fuente aleatoria de Internet

**▪ Email Honeypots:** también se llaman trampas de correo. No son más que direcciones de correo electrónico falsas que se utilizan específicamente para atraer correos electrónicos falsos y maliciosos de los adversarios.

**▪ Spider Honeypots:** también se conocen como trampas para arañas. Estos honeypots están diseñados específicamente para atrapar rastreadores web y spiders

**▪ Honeynets**:Son muy eficaces para determinar todas las capacidades de los adversarios. Las honeynets se implementan principalmente en un entorno virtual aislado junto con una combinación de servidores vulnerables.

**Honeypot Tools**

**▪ HoneyBOT 
Source:** https://www.atomicsoftwaresolutions.com

HoneyBOT is a medium interaction honeypot for windows. A honeypot creates a safe environment to capture and interact with unsolicited traffic on a network

▪ Blumira honeypot software (https://www.blumira.com)
▪ NeroSwarm Honeypot (https://neroswarm.com)
▪ Valhala Honeypot (https://sourceforge.net)
▪ Cowrie (https://github.com)
▪ StingBox (https://www.stingbox.com)