- Tags: #pasive_interface

Configurar una **interfaz pasiva** (Passive Interface) es una excelente práctica de seguridad y eficiencia. Su función es permitir que una interfaz siga perteneciendo al proceso de enrutamiento (para que su red sea anunciada a otros routers), pero **prohíbe que el router envíe o reciba actualizaciones de enrutamiento** por ese puerto.

Generalmente, esto se aplica a las interfaces **LAN** (como las GigabitEthernet que conectan a tus PCs), ya que los computadores no necesitan procesar paquetes de OSPF.

```cisco
RouterA>enable
RouterA#configure terminal
RouterA(config)#router ospf 10
RouterA(config-router)#passive-interface GigabitEthernet0/0
```


#### Opción B: "Default" (Recomendada por seguridad)

Esta es la forma más profesional. Pones todas las interfaces en modo pasivo por defecto y solo habilitas (con `no passive-interface`) aquellas que conectan con otros routers:

```cisco
RouterA(config)#router ospf 10
RouterA(config-router)#passive-interface default
RouterA(config-router)#no passive-interface Serial0/3/0
RouterA(config-router)#no passive-interface Serial0/3/1
```