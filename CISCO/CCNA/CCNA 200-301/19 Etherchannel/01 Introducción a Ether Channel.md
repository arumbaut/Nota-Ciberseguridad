- Tags: #etherchannel

Se utiliza ma para mejorar la conectividad de los usuarios ya que al agregar puertos a un mismo canal aumentan las vías por las que diferentes usuarios podrán utilizar la red dividiéndolos en cada uno de los canales y evitando sobrecarga de un puerto
Ether Channel tiene varias denominaciones

- Port Channel
- Link Aggregation
- Port Aggregation 

![[Pasted image 20260417203315.png|515]]

Ether Channel se utiliza con el objetivo de utilizar dos enlaces y crear redundancia utilizando estos dos enlaces como un único enlace virtual. Este link virtual permanecerá activo siempre y cuando una de las 2 conexiones físicas este activa

![[Pasted image 20260417203504.png|633]]


#### Ether Channel se puede configurar de varias maneras
Es recomendable utilizar las configuraciones que requiere control de protocolo. Si estamos trabajando con dispositivos Cisco es mejor utilizar *PAgP*  y si tenemos dispositivos de Cisco y de otro fabricante es recomendable *LACP*
	
![[Pasted image 20260417204044.png|660]]

Los puertos elegidos para Ether Channel deben coincidir en los dos SW

![[Pasted image 20260417204458.png|700]]

![[Pasted image 20260418100406.png|702]]

![[Pasted image 20260418100652.png|680]]