- Tags

Broadcast Domain: Es cuando un frame se envía desde un dispositivo y el sw lo reenvía hacia todos los puertos excepto desde donde se envió el frame. Es una función de la capa 2 por lo que funciona a nivel de MAC address
![[Pasted image 20260412122623.png|641]]

Imaginemos un escenario donde 2 redes distintas están conectadas a un mimo SW en los dos casos se estarían reenviando frame a los puertos de todos los equipos pues solo existe un Broadcast Domain y crearía una sobrecarga en el SW . Lo que ocurre es que a nivel de Red tenemos 2 redes L3 pero a nivel de L2 tenemos un solo broadcast domain y esto no es recomendable.  
![[Pasted image 20260412123039.png|688]]


Para solucionar esto es recomendable separar los Broadcast Domain (BC Domain) mediante SW
![[Pasted image 20260412123436.png|790]]

Podemos lograrlo mediante Vlans utilizando solamente un SW
![[Pasted image 20260412123608.png|726]]

