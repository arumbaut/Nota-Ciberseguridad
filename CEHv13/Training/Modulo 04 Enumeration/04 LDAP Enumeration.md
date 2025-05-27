
**LDAP Enumeration** – _Enumeración LDAP_  
LDAP es un protocolo de Internet para acceder a servicios de directorio distribuidos. LDAP accede a listados de directorios dentro de Active Directory o desde otros servicios de directorio. LDAP es una forma jerárquica o lógica de un directorio, similar al organigrama de una empresa.

**nmap -p 389 --script ldap.base='"cn=users,dc=CEH,dc=com ldap-brute "' \<Target IP Address\>**

#### **LDAP Enumeration Tools**

##### **▪ Softerra LDAP Administrator**
Fuente: [https://www.ldapadministrator.com](https://www.ldapadministrator.com)
Softerra LDAP Administrator es una herramienta de administración LDAP que funciona con servidores LDAP como Active Directory (AD), Novell Directory Services y Netscape/iPlanet. Permite navegar y gestionar directorios LDAP.

##### **▪ ldapsearch**
ldapsearch abre una conexión a un servidor LDAP, realiza la autenticación (bind) y efectúa una búsqueda usando los parámetros especificados. El filtro debe ajustarse a la representación en cadena de los filtros de búsqueda, tal como se define en la RFC 4515.

Si no se proporciona un filtro, se usa el filtro por defecto (objectClass=*).

The following command can be used to perform an LDAP search using simple authentication:

**ldapsearch -h \<Target IP Address\> -x Module**

The following command can be executed to obtain additional details related to the naming contexts:

**ldapsearch -h \<Target IP Address\> -x -s base namingcontexts**

The following command can be used to obtain more information about the primary domain:

**ldapsearch -h \<Target IP Address\> -x -b “DC=htb,DC=local”**

#### **Some additional LDAP enumeration tools:** 
▪ AD Explorer (https://docs.microsoft.com) 
▪ LDAP Admin Tool (https://www.ldapsoft.com) 
▪ LDAP Account Manager (https://www.ldap-account-manager.org) 
▪ LDAP Search (https://securityxploded.com)
