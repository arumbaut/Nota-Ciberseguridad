- Tags: #etherchannel #etherchannel_conf 


### Configuración Paso a Paso (LACP)
Imagina que quieres unir los puertos `GigabitEthernet0/1` y `0/2` de dos switches.

SW1
```cisco
SW1(config)# interface range g0/1 - 2
SW1(config-if-range)# channel-group 1 mode active  <-- Aquí creas el grupo
SW1(config-if-range)# exit

SW1(config)# interface port-channel 1             <-- Entras a la interfaz lógica
SW1(config-if)# switchport mode trunk             <-- Configuras el canal como Trunk

```

SW2
```cisco
SW2(config)# interface range g0/1 - 2
SW2(config-if-range)# channel-group 1 mode active
SW2(config-if-range)# exit

SW2(config)# interface port-channel 1
SW2(config-if)# switchport mode trunk

Verificar la configuracion
SW2# show etherchannel summary
SW2# show interface port-channel 1

```

### Para hacer una configuración utilizando PAgP es similar lo único a cambiar seria el **"idioma"** que hablan los switches para ponerse de acuerdo.

### Los "Estados" cambian de nombre

En lugar de usar `active` o `passive`, PAgP utiliza términos diferentes. Ejemplo
- **Desirable:** El switch toma la iniciativa y pregunta activamente al otro extremo si quiere formar un EtherChannel.
    
- **Auto:** El switch espera pasivamente a que el otro le pregunte. **Si pones ambos en `auto`, el enlace nunca subirá.**

```cisco

SW2(config)# interface range g0/1 - 2
SW2(config-if-range)# channel-group 1 mode desirable
SW2(config-if-range)# exit

SW2(config)# interface port-channel 1
SW2(config-if)# switchport mode trunk

Verificar la configuracion
SW2# show etherchannel summary
SW2# show interface port-channel 1
```