Probablemente la utilidad de red más usada sea ping. La mayoría de los dispositivos habilitados para IP admiten algún tipo de comando **ping** para probar si los dispositivos de red son accesibles o no a través de la red IP.

Si la configuración IP parece estar correctamente configurada en el host local, a continuación vuelva a probar la conectividad de red mediante el comando ping. El comando **ping** puede ir seguido de una dirección IP o del nombre de un host de destino. En el ejemplo, el usuario hace ping a la puerta de enlace predeterminada en 10.10.10.1 y luego hace ping a ww w.cisco.com.

![[Pasted image 20260327144257.png|689]]


Al enviar un comando ping a una dirección IP, se envía un paquete conocido como solicitud de eco a través de la red a la dirección IP especificada. Si recibe la solicitud de eco, el host de destino responde con un paquete denominado respuesta de eco. Si la fuente recibe la respuesta de eco, la respuesta de la dirección IP específica verifica la conectividad. El ping no se realiza correctamente si aparece un mensaje como tiempo de espera de solicitud o falla general.

Si se envía un comando **ping** a un nombre, como www.cisco.com, primero se envía un paquete a un servidor DNS para resolver el nombre en una dirección IP. Una vez obtenida la dirección IP, se reenvía la solicitud de eco a la dirección IP y se continúa el proceso. Si el comando ping enviado a la dirección IP funciona, pero el ping enviado al nombre no, es muy probable que exista un problema con DNS.

Si los comandos de **ping** enviados tanto al nombre como a la dirección IP son exitosos, pero el usuario aún no puede acceder a la aplicación, lo más probable es que el problema resida en la aplicación en el host de destino. Por ejemplo: quizás no se esté ejecutando el servicio solicitado.

Si no funciona ninguno de los dos comandos ping, es muy probable que el problema sea la conectividad de red en la ruta hacia el destino. De suceder esto, lo habitual es enviar un comando ping a la puerta de enlace predeterminada. Si este comando ping funciona correctamente, el problema no es local. Si el comando ping enviado a la puerta de enlace predeterminada falla, entonces el problema reside en la red local.

En algunos casos, el ping puede fallar pero la conectividad de red no es el problema. Un ping puede fallar debido al cortafuegos en el dispositivo emisor o receptor, o un enrutador en la ruta que está bloqueando los pings.

El comando **ping** básico suele enviar cuatro ecos y esperar respuestas para cada uno. Sin embargo, esto se puede modificar para incrementar su utilidad. Las opciones presentadas en la figura muestran características adicionales disponibles.
![[Pasted image 20260327144400.png|705]]