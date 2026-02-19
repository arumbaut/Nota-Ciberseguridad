- Tags : #reverse_shell #groovy_script #jenkins #impacket #impacket_smbserver

![](../../../attachments/Pasted%20image%2020260217093755.png)

![](../../../attachments/Pasted%20image%2020260217093857.png)

![](../../../attachments/Pasted%20image%2020260217094046.png)

Buscamos en internet **Grovy Script Reverse Shell** , hay que tener en cuenta el tipo de servidor si es windows o linux porque en dependencia de esto cambia la ejecución.

**Grovy Script Reverse Shell**: [https://dzmitry-savitski.github.io/2018/03/groovy-reverse-and-bind-shell](https://dzmitry-savitski.github.io/2018/03/groovy-reverse-and-bind-shell)

![](../../../attachments/Pasted%20image%2020260217095542.png)

Para windows solo cambiaríamos el script que se introduce en la consola
*Recurso Linux*: [https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6](https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6)
*Recurso Window*: [https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6](https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6)

Básicamente la diferencia en el payload es 
```bash
#Para windows utilizamos esta linea  
String cmd=”cmd.exe”;

#Para Linux utilizamos esta
String cmd="/bin/sh";

```

T ambien desde windows podemos ejecutar comando para copiar cosas al servidor mediante *smb*

Nos levantamos un recurso compartido desde nuestra maquina atacante

```bash
impacket-smbserver recurso $(pwd) -smb2support
```

Desde la consola de Jenkins Accedemos al recurso para ejecutar el nc.exe y enviarnos una consola cmd a nuestra maquina
![](../../../attachments/Pasted%20image%2020260217102131.png)

