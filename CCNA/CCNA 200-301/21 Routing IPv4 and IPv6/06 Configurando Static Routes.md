
### Escenario que implementaremos

##### Solo nos enfocaremos en la configuración de las rutas estáticas(*S* ) de os Routers A y B
![[Pasted image 20260421093710.png|753]]


### Router A
```cisco
RouterA>enabe
RouterA#show ip route   #Muestra la table de Rutas
RouterA#configure terminal
RouterA(config)#ip route 192.168.10.0 255.255.255.0 172.16.0.2
```

### Router B
```cisco
RouterB>enabe
RouterB#show ip route   #Muestra la table de Rutas
RouterB#configure terminal
RouterB(config)#ip route 10.0.0.0 255.255.255.0 172.16.0.1
```

Las rutas también se pueden indicar mediante la interface de salida del dispositivo , es la que esta de cara a la red que queremos alcanzar. Se recomienda utilizar la ip en lugar de la interface de salida
```cisco
RouterB(config)#ip route 10.0.0.0 255.255.255.0 f0/0
```

Podemos hacer ping desde un router indicándole desde que ip queremos original el paquete siempre que la ip pertenezca a una de las interfaces del router
```cisco
RouterB#ping 192.168.10.8 source 10.0.0.1
```

También se puede establecer una conexión ssh
```cisco
RouterB#ssh -l user 10.0.0.1

```

Podemos utilizar en nuestros equipos los comandos ping y tracert para diagnosticar donde hay un fallo en la conexión de nuestra ruta . tracert -d hace que se ejecute mas rápido el proceso de tracert 