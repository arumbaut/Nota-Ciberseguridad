

![[Pasted image 20260427153808.png|637]]

Empezaremos :
Al ser una ACL Standard seleccionaremos los paquetes basados en el *Source IP* 
- Queremos permitir el trafico desde 10.0.0.10 hacia el servidor [ permit host 10.0.0.10 ]
- Le daremos un nombre a la ACL [ ip access-list standard DEMO ]
- Aplicamos la *ACL*  a una de las interfaces como trafico entrante o saliente **(inbound , outbound)**.  [ interface F0/0 access-group DEMO in ]
- Por cada interface puedo tener **una ACL Inbound y una ACL Outbound** por cada protocolo L3

*Outbound :* Es el trafico que abandona la interface
*Inbound :* Es el trafico que entra en la interfac

# Importante para aplicar ACL Standard en el examen CCNA, regla de cisco.
-
#regla_standard_acl
#### "Regla: Las listas de control de acceso estándar se aplican en la interfaz del router más cercana al dispositivo de destino." Actualmente no se aplica este criterio debido a lo desarrollado de los dispositivos . Solo valoramos que se aplique bien la regla

![[Pasted image 20260427161510.png|751]]