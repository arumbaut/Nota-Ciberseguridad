![[Pasted image 20260506184134.png]]


### Firewall sin Estado (Primera Generación)
- Examina la capa de los protocolos de la capa de transporte y enrutamiento como las direcciones de red de origen y destino los protocolos y los números de puerto.
- Las políticas de FW utilizan estos atributos para definir que paquetes se aprueban
- La reglas se ordenan en una lista y las coincidencia potencial se hacen de arriba hacia abajo
- La ultima política puede ser implícita denegando el paquete de manera predeterminada o explicita haciendo la acción configurada correspondiente, aprobando o denegando el paquete
- Si la poética coincide con la dirección de origen y destino , el numero de puerto y el protocolo el paquete se acepta de lo contrario se descarta o se bloquea silenciosamente

![[Pasted image 20260506184317.png]]

Inconveniente de los FWs sin estado es que necesita una configuración adicional para ofrecer un nivel de protección adecuado, necesita una política adicional para el trafico de retorno en una sesión, no administra adecuadamente los protocolos. 
Necesitan abrir un amplio rango de puertos para acomodar protocolo que usan puertos aleatorios y conexiones multiples como FTP con sus conexiones de control y datos. Usan un enfoque universal para decidir si aprueban o no el trafico. Debido  a este enfoque abierto los actores maliciosos pueden evadir potencialmente las reglas del firewall e inyectar paquetes no autorizados a través de puertos y protocolos aceptables

![[Pasted image 20260507005000.png]]

### Segunda Generación (FW con Estado)

Compensa las limitaciones de la primera generación FW sin estado desarrollando criterios adicionales para aprobar o bloquear el trafico. Esta diseñado para observar las conexiones de red  a lo largo del tiempo mediante el seguimiento de comprobación de 5 tuplas y el estado de la conexión en su tabla de sesiones. Observa como se establecen nuevas conexiones de red y examina como el trafico va y viene si una conexión se comporta inadecuadamente o el trafico de retorno no coincide con el trafico de entrada correspondiente bloquea esa conexión

![[Pasted image 20260507005807.png|697]]

![[Pasted image 20260507005830.png|701]]

### Tercera Generación

![[Pasted image 20260507010118.png]]

### Next Generation Firewall
![[Pasted image 20260507010340.png]]
![[Pasted image 20260507010438.png]]

![[Pasted image 20260507010522.png]]

![[Pasted image 20260507010732.png]]

![[Pasted image 20260507010903.png]]
