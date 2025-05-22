## Information Security - InfoSec

**Es la práctica de proteger la información mitigando los riesgos de la información.Se basa en cinco elementos principales:** **confidencialidad, integridad, disponibilidad, autenticidad y no repudio.**

## CIA Triad

**▪ Confidentiality**
La confidencialidad es la garantía de que la información solo sea accesible para personas autorizadas. Las violaciones a la confidencialidad pueden ocurrir por un mal manejo de los datos o por intentos de hackeo.

**▪** **Integrity**:
La integridad es la confiabilidad( **trustworthiness** ) de los datos o recursos en la prevención de cambios indebidos y no autorizados —la garantía de que la información es suficientemente precisa para su propósito.

**▪** **Availability**
La disponibilidad es la garantía de que los sistemas responsables de entregar, almacenar y procesar información estén accesibles cuando los usuarios autorizados lo requieran.

**Authenticity**
La autenticidad se refiere a la característica de la comunicación, los documentos o cualquier dato que garantiza su calidad de ser genuino o no estar corrompido. El principal propósito de la autenticación es confirmar que un usuario es auténtico. Controles como la biometría, las tarjetas inteligentes y los certificados digitales aseguran la autenticidad de los datos, las transacciones, las comunicaciones y los documentos.

**Non-Repudiation** 
El no repudio es una forma de garantizar que el remitente de un mensaje no pueda negar posteriormente haberlo enviado y que el destinatario no pueda negar haberlo recibido. Las personas y organizaciones utilizan firmas digitales para asegurar el no repudio.

### Information Security Attacks: Motives, Goals, and Objectives

**Attacks = Motive (Goal) + Method (TTPs)** + **Vulnerability**        

**(TTPs) => Tactics, Techniques, andProcedures **

🛡️**Tácticas**
Las “tácticas” son las directrices que describen la forma en que un atacante lleva a cabo el ataque desde el principio hasta el final.  
Estas directrices comprenden varias tácticas para la recopilación de información, realizar explotación inicial, escalamiento de privilegios, movimiento lateral, y aplicar medidas para acceso persistente al sistema y otros fines.

🛠️**Técnicas**
Las “técnicas” son los métodos técnicos utilizados por un atacante para lograr resultados intermedios durante el ataque.  
Estas técnicas incluyen la explotación inicial, el establecimiento y mantenimiento de canales de comando y control, el acceso a la infraestructura objetivo, el encubrimiento de la exfiltración de datos, entre otros

🗂️ **Procedimientos**
Las “procedimientos” son enfoques organizativos que los actores de amenazas siguen para lanzar un ataque.  
El número de acciones normalmente varía dependiendo de los objetivos del procedimiento y del grupo de actores de amenazas

**Vulnerability**: Una vulnerabilidad se refiere a una debilidad en el diseño o implementación de un sistema que puede ser explotada para comprometer la seguridad del sistema.

## Attack Classification

### Passive attack

**Passive Attacks**

Los ataques pasivos implican interceptar y monitorear el tráfico de la red y el flujo de datos en la red objetivo y no alteran los datos. Los atacantes realizan reconocimiento de las actividades de la red utilizando sniffers.

**Examples of passive attacks:**
  
1. **Footprinting**

2. **Sniffing and eavesdropping**

3. **Network traffic analysis**

4. **Decryption of weakly encrypted traffic**

### Active attack

**Active Attacks**

Los ataques activos alteran los datos en tránsito o interrumpen la comunicación o los servicios entre los sistemas para eludir o penetrar en sistemas asegurados. Los atacantes lanzan ataques al sistema o red objetivo enviando tráfico activamente que puede ser detectado.

| Denial-of-service (DoS) attack<br><br> Bypassing protection mechanisms<br><br> Malware attacks (such as viruses, worms, ransomware)<br><br> Modification of information<br><br> Spoofing attacks<br><br> Replay attacks<br><br> Password-based attacks<br><br> Session hijacking | Man-in-the-Middle attack<br><br> DNS and ARP poisoning<br><br> Compromised-key attack<br><br> Firewall and IDS attack<br><br> Profiling o Arbitrary code execution<br><br> Privilege escalation<br><br> Backdoor access<br><br> Cryptography attacks |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
### Close-in attack

Los ataques cercanos se realizan cuando el atacante está en proximidad física cercana al sistema o red objetivo.

### Insider attack

Los ataques internos son realizados por personas de confianza que tienen acceso físico a los activos críticos del objetivo. Un ataque interno implica el uso de acceso privilegiado para violar normas o causar intencionalmente una amenaza a la información o los sistemas de información de la organización.

**Examples of insider attacks:**

- Eavesdropping and wiretapping     
- Shoulder surfing passwords
- Theft of physical devices
- Social engineering
- Data theft and spoliation
- Pod slurping
- Planting keyloggers, backdoors, or malware

## Distribution Attacks

Distribution attacks occur when attackers tamper with hardware or software prior to installation. Attackers tamper the hardware or software at its source or when it is in transit**. (**Los ataques de distribución ocurren cuando los atacantes manipulan el hardware o software antes de su instalación. Pueden alterar los componentes en su origen o mientras están en tránsito.**)**
## Information Warfare

El término guerra de la información o InfoWar se refiere al uso de las tecnologías de la información y la comunicación (TIC) para obtener ventajas competitivas sobre un oponente.