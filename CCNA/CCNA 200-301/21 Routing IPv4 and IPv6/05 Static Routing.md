- Tags: #routing 

Cuando tenemos redes directamente conectadas a un dispositivo de Router nos es necesario configurar ninguna ruta porque este ya se encarga de esto creándolas. La creación de rutas de forma statica comienza cuando tenemos mas de un dispositivo de Router  

![[Pasted image 20260421090326.png|761]]

En este caso tenemos 2 Routers conectado pero sin tener configurada ninguna ruta manual solo las que el mismo genera de las redes conectadas directamente. Esto presupone un problema ya que el Router A no tiene forma de saber como llegar a la red *192.168.10.0/24* , aqui es donde entra en juego las rutas Estatificas  

![[Pasted image 20260421092721.png|709]]

Routers con las direcciones estáticas configuradas para permitir el trafico de una red a otra
![[Pasted image 20260421093435.png|754]]