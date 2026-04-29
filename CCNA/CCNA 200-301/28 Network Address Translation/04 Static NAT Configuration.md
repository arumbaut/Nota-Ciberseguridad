![[Pasted image 20260428160012.png]]

Como Tenemos una red /29 tenemos varias direcciones para el NAT ESTÁTICO por lo que a las *IP Internas*  se le puede Natear una *IP Publica*

Lo primero es decirle al router  que interfaces están en la *Red Externa* y cuales en la *Red Interna*

Lo que esto hace es decirle al Router en que dirección va a procesar el trafico 

```cisco
Router0>enable
Router0#configure termina

Router0(config)#int f0/0
Router0(config-if)#ip nat inside
Router0(config-if)#exit
Router0(config)#int f0/1
Router0(config-if)#ip nat outside

Habiendo declarado las interfaces internar y externas pasamos a la creacion de la NAT Statica

Router0(config)#ip nat inside source static 10.0.0.80 203.0.113.3


Limpiar tabla de NAT
Router0#clear ip nat translation *
  
```


Variaciones de concepto inside y outside:

### 1. El estándar: `inside` hacia afuera (La mayoría de los casos)

Como vimos en tu comando `ip nat inside source static 10.0.0.80 203.0.113.3`, se mapea una IP privada interna a una pública externa.

- **Dirección:** De una IP interna a una IP externa.
    
- **Uso:** Publicar un servidor web o de base de datos interno para que sea accesible desde Internet.
    

### 2. El caso inverso: `ip nat outside source static`

Aunque es menos frecuente, existe el NAT estático de **afuera hacia adentro**.

- **¿Para qué sirve?** Se usa cuando quieres que una IP de "Internet" aparezca ante tus dispositivos internos como si fuera una IP de tu propia red local.
    
- **Ejemplo:** Tienes un servidor en otra empresa con IP `8.8.8.8`, pero por seguridad o enrutamiento, quieres que tus PCs internas lo vean como la IP `10.0.0.200`.
    

### En el NAT estático **estricto**, sí, es una relación **uno a uno**. Una IP privada se "casa" con una IP pública y nadie más puede usar esa IP pública.

Sin embargo, hay una variante del NAT estático que no es de "IP a IP", sino de **"Puerto a Puerto"** (Static Port Translation o Port Forwarding):

- **Comando:** `ip nat inside source static tcp 10.0.0.80 80 203.0.113.3 8080`
    
- **Qué hace:** Aquí no mapeas toda la IP, sino solo un servicio. Si alguien entra a la IP pública por el puerto `8080`, el router lo envía a la PC interna al puerto `80`.
    
- **Ventaja:** Puedes usar una sola IP pública para dar acceso a varios servidores internos diferentes (uno por el puerto 80, otro por el 443, etc.).