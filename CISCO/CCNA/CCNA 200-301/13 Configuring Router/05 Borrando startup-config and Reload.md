- Tags : #router_borarr_startup_config

```cisco
#Borramos el sartup-config es lo almacenado en la nvram
RouterPrimario#erase startup-config

#Recargamos el router para poder tenerlo de fabrica porque actualmente esta ejecutando lo que esta en la ram y esta no se puede borrar. Solo se borra si se apaga el equipo.
RouterPrimario#reload


```
