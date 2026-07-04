

![[Pasted image 20260421071415.png|790]]

![[Pasted image 20260421071600.png|799]]

El mensaje se va formando de dentro hacia afuera empezando por la data que seria en este caso el protocolo *ICMP*  que va dentro del Packet y luego se crea el *Frame* al cual se le integra el *Packet*  , o interesante que al momento de crear el frame tenemos la *Source MAC Addres*  que no es mas que la MAC del equipo que envía el *Mensaje*  pero no tenemos la *Destination MAC Address* por lo que se necesita otro protocolo *ARP*  para identificar esta *Destination MAC Address*