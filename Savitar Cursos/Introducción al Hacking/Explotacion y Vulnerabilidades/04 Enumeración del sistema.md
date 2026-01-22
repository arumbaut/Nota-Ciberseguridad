- Tags #enumeration #tools #recursos_github #reconocimiento_tools #ps_commands #scripts


 La enumeración es un proceso crítico para identificar por ejemplo vías potenciales de poder elevar nuestros privilegios de usuario, así como para comprender la estructura del sistema objetivo y encontrar información útil para futuros ataques.

Algunas de las herramientas que vemos en esta clase son:

- **LSE** (**Linux Smart Enumeration**): Es una herramienta de enumeración para sistemas Linux que permite a los atacantes obtener información detallada sobre la configuración del sistema, los servicios en ejecución y los permisos de archivo. LSE utiliza una variedad de comandos de Linux para recopilar información y presentarla en un formato fácil de entender. Al utilizar LSE, los atacantes pueden detectar posibles vulnerabilidades y encontrar información valiosa para futuros ataques.
- **Pspy**: Es una herramienta de enumeración de procesos que permite a los atacantes observar los procesos y comandos que se ejecutan en el sistema objetivo a intervalos regulares de tiempo. Pspy es una herramienta útil para la detección de malware y backdoors, así como para la identificación de procesos maliciosos que se ejecutan en segundo plano sin la interacción del usuario.

- **Herramienta LSE**: [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)
- **Herramienta LinEnum**: https://github.com/rebootuser/LinEnum
- **Herramienta PSPY**: [https://github.com/DominicBreuker/pspy](https://github.com/DominicBreuker/pspy)

Recursos Web para detectar vulnerailidades SUID
- **gtfobins**: https://gtfobins.github.io/#
- **Hacktricks**: https://book.hacktricks.wiki/en/index.html

Ver los comandos que se estan ejecutando en el sitema con ps
```
ps -eo user,command
```

Scripts manual
```
#!/bin/bash

function ctrl_c(){
    echo -e "\n\n[!] Saliendo...\n"
    tput cnorm; exit 1
}

# Ctrl+C
trap ctrl_c SIGINT

old_process=$(ps -eo user,command)

tput civis # Ocultar cursor

while true; do
    new_process=$(ps -eo user,command)
    diff <(echo "$old_process") <(echo "$new_process") | grep "[\>|<]" | grep -vE "command|kworker|procmon"
    old_process=$new_process
done
```