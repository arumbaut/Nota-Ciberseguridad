SPL : Search Processing Language 

2 Tipos de búsquedas 

Raw event searches: Búsquedas que solo recuperan eventos de un indice o indices , se ejecutan normalmente cuando no se desea analizar un problema. No suelen incluir comandos de búsqueda

SPL: Busqueda Basica
### Ej:
#### index=botsv3 earliest=0 sourcetype=syslog

Transforming Searches: Búsqueda que realiza algún tipo de modificación o calculo estadístico sobre un conjunto de resultados.

SPL: Busqueda Basica | Transformacion  [ | Trasnformacion o Filtro ] *
### Ej:
#### index=botsv3 earliest=0 sourcetype=syslog | stats count by host

![[Pasted image 20260518220942.png]]

![[Pasted image 20260518221102.png]]

## SPL Consults

![[Pasted image 20260518223105.png]]

![[Pasted image 20260518223521.png]]

![[Pasted image 20260518223622.png]]

![[Pasted image 20260518223744.png]]

![[Pasted image 20260518223843.png]]

![[Pasted image 20260518224049.png]]

![[Pasted image 20260518224230.png]]

![[Pasted image 20260518224350.png]]

Para comentar una parte del código SPL lo encerramos entre \`\`\`  \`\`\`.

![[Pasted image 20260518224557.png]]

![[Pasted image 20260518224936.png]]

![[Pasted image 20260518225106.png]]

![[Pasted image 20260518230131.png]]

![[Pasted image 20260518230436.png]]

![[Pasted image 20260518230801.png]]

![[Pasted image 20260518230828.png]]

![[Pasted image 20260518232343.png]]

![[Pasted image 20260518232655.png]]

![[Pasted image 20260518232813.png]]

![[Pasted image 20260518232910.png]]

![[Pasted image 20260518232923.png]]

![[Pasted image 20260518232937.png]]

![[Pasted image 20260518233006.png]]

![[Pasted image 20260518233014.png]]

![[Pasted image 20260518233031.png]]

![[Pasted image 20260523101556.png]]

![[Pasted image 20260518233130.png]]


Para sacar valores estadísticos

![[Pasted image 20260523101801.png]]

![[Pasted image 20260523101925.png]]

![[Pasted image 20260523102141.png]]
Se puede poner por hora por mes año

![[Pasted image 20260523173202.png]]