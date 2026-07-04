- Tags: #3. #RapidSpanningTreeProtocol_RSTP #RSTP

En el STP normal, si el camino principal falla, el switch tiene que volver a calcular todo. En **RSTP**, el switch ya tiene identificado un **"Alternate Port"** (un camino de reserva ya calculado). Si el principal cae, el puerto alternativo pasa a _Forwarding_ casi de inmediato.

La diferencia fundamental es la **velocidad de convergencia**: cuánto tiempo tarda la red en recuperarse si un cable se rompe o un switch se apaga.


![[Pasted image 20260417150547.png|479]]

![[Pasted image 20260417151135.png|661]]

### Habilitar RSPT

```cisco
sw(config)#spanning-tree mode rapid-pvst
```

![[Pasted image 20260417151717.png]]