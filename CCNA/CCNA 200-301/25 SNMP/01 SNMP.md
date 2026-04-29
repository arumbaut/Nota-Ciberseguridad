- Tags : #snmp  


SNMP tiene varias versiones 

SNMPv1 y SNMPv2 son muy similares por eso explicaremos la 2.

**SNMPv2c**  : 
- Utiliza un string comunitario para autenticarse, que no es mas que una palabra no encriptada que se utiliza para la autenticación en el SNMP manager
- Se pueden establecer 2 *commuity strings*  una para *el acceso de solo lectura*  y otra para **accesos de escritura y lectura**
- Es relativamente insegura, y es ampliamente implementada y utilizada

**SNMPv3**  : 
- Es la version mas reciente de SNMP
- A esta version se agrego algo conocido como *SNMP view*
	- Configura el agente para solo permitir el acceso de ciertos *MIBs* (Management Information Base o **Base de Información de Gestión**) desde el servidor o el administrador.
- Encripta toda la comunicación
- Autentica los dispositivos brindando diferentes niveles de seguridad