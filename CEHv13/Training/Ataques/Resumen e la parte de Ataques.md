- **Ubicación del archivo SAM:**  
    `%SystemRoot%\system32\config\SAM`  
    (normalmente en `C:\Windows\System32\config\SAM`)
    
- **Registro del sistema:**  
    Windows monta este archivo en el registro bajo la clave:  
    `HKEY_LOCAL_MACHINE\SAM`
#### Tools to Extract the Password Hashes 
**▪ pwdump7**  
==▪ Mimikatz== 
▪ DSInternals 
▪ hashcat
▪ PyCrack 

**Nota:** **==Los usuarios con el User ID 500 son administradores de sistema, con 501 invitados==**

**==Types of Password Attacks==**
**Rainbow table attack**
En un ataque de tabla arcoíris, el atacante crea una tabla con una gran lista de contraseñas posibles y sus respectivos valores hash

**Distributed Network Attack**
Es una técnica utilizada para recuperar archivos protegidos por contraseña, aprovechando la potencia de procesamiento no utilizado de máquinas distribuidas a través de una red para descifrar contraseñas

**▪ Rule-based Attack)**
==Los atacantes utilizan este tipo de ataque cuando obtienen información previa sobre la contraseña==.

**▪ Hybrid Attack**
==Combina un ataque de diccionario con modificaciones como la adición de números o símbolos para descifrar contraseñas.==

**▪ Syllable Attack)**
 ==cuando las contraseñas no son palabras conocidas. En estos casos, utilizan diccionarios modificados y generan todas las combinaciones posibles de sílabas para intentar descifrarlas.==

**▪ Password Spraying Attack**
==Consiste en probar una o pocas contraseñas comunes en múltiples cuentas al mismo tiempo

**▪ Mask Attack**
==Similar a un ataque de fuerza bruta, pero se enfoca en recuperar contraseñas de hashes utilizando un conjunto más específico de caracteres basado en la información que el atacante conoce==

 ==**hashcat**==
 **Ataques de fuerza bruta (brute-force); 
Ataques por diccionario (dictionary attacks); 
Ataques con máscara (mask attacks)

```
hashcat -a 3 -m 0 md5_hashes.txt ?l?l?l?d?d?d

-a → Specifies the attack mode, which is 3 here (brute-force attack)

-m → Specifies the hash type, which is 0 here (MD5)
```

#### ==**▪ Hash Injection/Pass-the-Hash (PtH) Attack**==
==los atacantes inyectan un hash comprometido de LanMan (LM) o NTLM en una sesión local y luego usan ese hash para autenticar el acceso a los recursos de la red

==**▪ Internal Monologue Attack**==
el atacante utiliza SSPI(Security Support Provider Interface) para realizar una autenticación NTLM. el atacante hace una llamada interna al sistema para calcular la respuesta NetNTLM, 

**▪ Cracking Kerberos Password**

==**Kerberoasting*==
un atacante utiliza una cuenta de usuario común o un usuario con credenciales válidas del dominio para solicitar ==tickets de concesión de servicio (TGS)== para cuentas de servicio, TGS pueden estar cifradas con el hash de la contraseña de la cuenta de servicio usando el algoritmo RC4.El atacante extrae estos tickets de la memoria o del tráfico de red e intenta descifrarlos de manera offlin

**AS-REP Roasting**
 ==Los atacantes apuntan a usuarios que tienen habilitada la opción **“No requerir preautenticación Kerberos”** en las opciones de su cuenta, o a cuentas de usuario que no requieren preautenticación==.
 Los atacantes aprovechan vulnerabilidades en el proceso de autenticación inicial (AS-REP) para obtener un ==TGT== y luego intentar descifrarlo.

####**▪ Pass-the-Ticket Attack**
Es una técnica utilizada para autenticar a un usuario en un sistema que utiliza tickets de Kerberos sin necesidad de proporcionar la contraseña del usuario
Para realizar este ataque, el atacante extrae los tickets Kerberos de cuentas legítimas utilizando herramientas de extracción de credenciales. Se puede capturar un TGT (Ticket Granting Ticket) o un ST (Service Ticket), dependiendo del nivel de acceso que se le haya permitido al cliente.

**Solicitud de tickets Kerberos:**
**TGT (Ticket Granting Ticket)**: Usado para solicitar un **ST (Service Ticket)** a través de la **TGS (Ticket Granting Service),** lo que da acceso a todos los servicios que el cliente tiene autorizados.

**ST (Service Ticket)**: Usado para acceder a un servicio específico.

**Tipos de tickets:**
**Silver Tickets:** Estos son los tickets capturados para acceder a servicios específicos dentro de la red que utilizan Kerberos.  **==Para obtener acceso a un servicio específico,==** 

**Golden Tickets:** Son los más poderosos y peligrosos. Se capturan utilizando el hash NTLM de KRBTGT (el servicio de tickets Kerberos) en el dominio. Con el hash de KRBTGT, el atacante puede generar TGTs válidos para cualquier cuenta en el directorio activo, dándole acceso total a los recursos y servicios del dominio.

**Attackers use tools such as** 
==Mimikatz,==  Permite a los atacantes pasar el TGT de Kerberos a otras computadoras e iniciar sesión usando el ticket de la víctima.
==Rubeus,== 
==Windows Credentials Editor==

**▪ NTLM Relay Attack**
Un atacante intercepta y retransmite solicitudes de autenticación NTLM entre un cliente y un servidor para suplantar al cliente y obtener acceso no autorizado a recursos de la red.
Para realizar este ataque utilizamos la hrramienta 
==**Responder**==

**Password Recovery Tools**
**▪ Elcomsoft Distributed Password Recovery**
**▪ Passware Kit Forensic 
==**▪ hashcat== 
**▪ PCUnlocker 
**▪ Lazesoft Recover My Password **
**▪ Passper WinSenior **

####**Password-Cracking Tools** 
**▪ L0phtCrack**  
**▪ THC-Hydra 
▪ RainbowCrack  

Vulnerability Exploitation
▪ Exploit Database  
▪ OSV 
 ▪ VulDB
 ▪ MITRE CVE 
#### Herramientas de Explotación de Vulnerabilidades Impulsadas por IA  
**Nebula** 
**DeepExploit**  utiliza un modelo de aprendizaje profundo para automatizar la identificación y explotación de vulnerabilidades

 ==**Buffer Overflow**== 
**▪ Desbordamiento de Búfer Basado en Pila (Stack-Based Buffer Overflow) (Memoria estatica)**  
==En la mayoría de las aplicaciones, se utiliza una pila (stack) para la asignación de memoria estática==. ==Se asignan bloques contiguos de memoria para una pila que almacena variables temporales creadas por una función. La pila almacena las variables en orden "Último en Entrar, Primero en Salir" (LIFO, por sus siglas en inglés). Cada vez que se llama a una función, la memoria requerida para almacenar las variables se declara en la pila, y cuando la función termina, la memoria se libera automáticamente.==
==Para entender el desbordamiento de búfer basado en pila, se debe prestar especial atención a los registros **EBP**, **EIP** y **ESP**.==  

**▪ Heap-Based Buffer Overflow (Memoria Dinamica)** 
==El desbordamiento basado en heap ocurre cuando se asigna un bloque de memoria al heap y se escribe datos sin verificar los límites. Esta vulnerabilidad puede causar la sobreescritura de enlaces a asignación dinámica de memoria (punteros a objetos dinámicos), encabezados del heap, datos basados en heap, tablas de funciones virtuales, entre otros==

#### Heap Spraying 
La técnica de heap spraying consiste en ==saturar el espacio libre del heap de memoria de un proceso objetivo escribiendo múltiples copias de código malicioso en ubicaciones específicas de memoria==, explotando vulnerabilidades basadas en memoria como los desbordamientos de buffer

#### JIT Spraying 
Los atacantes utilizan técnicas de JIT spraying (Just-In-Time spraying) para ejecutar código arbitrario en el sistema de la víctima aprovechando vulnerabilidades en la función de compilación ==JIT presente en muchos navegadores web modernos==

#### Buffer Overflow Detection Tools
▪ OllyDbg 

**Escalating Privileges**
**DLL Hijacking**

**Attackers use tools such as** 
**Spartacus,** 
**DLLirant,**
**ImpulsiveDLLHijack,** 
**PowerSploit** 

**Spectre Vulnerability**
Esta falla permite a los atacantes engañar al procesador para que utilice la ejecución especulativa y acceda a datos restringidos.Afecta a muchos procesadores modernos, incluidos los de **Apple, AMD, ARM, Intel, Samsung y Qualcomm.**

**Meltdown Vulnerability**
Esta vulnerabilidad permite a los atacantes forzar un proceso para que acceda a memoria fuera de sus límites al explotar mecanismos de optimización de CPU, como la ejecución especulativa

**Privilege Escalation Tools**
**▪ BeRoot** is a post-exploitation tool to check common misconfigurations to find a way to escalate privilege.

**▪ pwncat** allows attackers to locate and exploit vulnerabilities associated with user accounts and session for privilege escalation.

**==pwncat$ escalate list -u root==**

▪ PowerSploit  
▪ Traitor 
▪ PEASS-ng  
▪ FullPowers
