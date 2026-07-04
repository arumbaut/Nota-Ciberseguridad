- Tags: #vlan #vlan_nativa

Problemas de seguridad de las VLAN

VLAN Hopping o Salto de VLAN

Se produce cuando utilizamos una cosa llamada *double tagging* . Este tipo de ataque en una red es posible pero no en los dispositivos modernos de cisco. Para fines educativos con un dispositivo viejo de cisco o que no este configurado contra este tipo de ataques pues utilizando un software especializado pudiéramos agregarle la cabecera de frame  802.1Q y decirle que la primera etiqueta de VLAN es la Vlan1 y las 2 es de la Vlan10.

Lo que pasara es que el primer dispositivo recibirá el paquete le quitara la primera etiqueta de la Vlan1 y seguirá el paquete con la etiqueta de la Vlaln2 por lo que pasara al otro dispositivo por la 2 Vlan etiquetada aun partiendo desde la 1 . Repetimos es algo que pasaba por la forma en que los dispositivos de cisco manejaban los paquetes antiguamente

