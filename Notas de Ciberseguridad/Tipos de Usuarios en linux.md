## **Usuarios con privilegios de administrador**

En Linux, los usuarios con UID = **0** son root (administrador).

`grep 'x:0:' /etc/passwd`

## **Usuarios normales (humanos)**

Normalmente, en distribuciones modernas, los **usuarios humanos** tienen UID ≥ 1000.

`awk -F: '$3 >= 1000 && $3 < 65534 {print $1}' /etc/passwd`

## **Cuentas de sistema / servicio**

Las cuentas de sistema suelen tener UID < 1000 (excepto root) y muchas usan shells como `/usr/sbin/nologin` o `/bin/false` para evitar login interactivo.


`grep -E 'nologin|false' /etc/passwd`


**Resumen visual de comandos:**


```
# Admins 
grep 'x:0:' /etc/passwd  

# Usuarios humanos 
awk -F: '$3 >= 1000 && $3 < 65534 {print $1}' /etc/passwd  

# Cuentas de sistema 
grep -E 'nologin|false' /etc/passwd
```