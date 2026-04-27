Descargamos Splunk ya sea para Linux Windows o Mac

```bash
#En un Ubuntu
tar -xvf splunk.tgz

#Creamos un user para ejecucion de splunk
useradd -m splunk -s /bin/bash

#Le ponemos un pasword
passwd splunk

chown -R splunk:splunk splunk

#Creamos las credenciales para splunk
nano splunk/etc/system/local/user-seed.conf
[user-ifo]
USERNAME=ruben
PASSWORD=ruben

/opt/splunk/bin/splunk start --accept-licence

#Habilitarlo para que inicie cuando se arranque la maquina
/opt/splunk/bin/splunk enable boot-start --user splunk

#Apagar el servicio
/opt/splunk/bin/splunk stop

```