- Tags: #nat_dinamico

Este es el mas utilizado ya que con una IP Publica podemos podemos hacer NAT de *varias direcciones IP Privadas*

![[Pasted image 20260428171135.png|788]]
![[Pasted image 20260428171234.png|711]]

## Funcionamiento del Dynamic NAT

![[Pasted image 20260428171851.png]]

![[Pasted image 20260428171951.png]]

![[Pasted image 20260428172115.png]]

![[Pasted image 20260428172220.png]]

![[Pasted image 20260428172825.png]]

![[Pasted image 20260428172901.png]]

Cuando otra maquina hace la misma petición al puerto 80 del servidor 52.26.45.240 si utiliza el mismo puerto local 49227 el router se da cuenta de que este ya esta pues el *Inside Global Port* lo cambia normalmente por el siguiente puerto disponible en el rango. Haciendo que aunque 2 PCs tengan el mismo *Inside Local Port*    van a tener un Único *Inside Global Port*. Permitiendo que los 2 equipos se comuniquen con el servidor al mismo tiempo sin ningún problema

![[Pasted image 20260428173200.png]]

![[Pasted image 20260428180246.png]]

![[Pasted image 20260428180516.png]]

![[Pasted image 20260428180539.png]]

![[Pasted image 20260428180553.png]]

![[Pasted image 20260428180605.png]]