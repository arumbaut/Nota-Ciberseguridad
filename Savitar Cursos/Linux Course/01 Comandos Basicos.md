```
Nos dice que usuario soy
whoami 

Muestra los grupos a los que pertenece el usuario y su id
id user 

Para aplicar filtros
| grep "asdasd" -n 

Nos da la ruta absluta de un comando por los tanto verifica si existe
which comando    ||  command -v comando


Ver los tipos de shell
cat /etc/shells

```

Ejecutar comandos en una linea. Los separamos con ;
```
whoami ; ls
```

Tenemos el && que ejecuta el 2 comando si el código de estado del primero fue exitoso
```
whoami && ls
```

Ver código de estado 
```
echo $?   # 0 exitoso  distinto de 0 no exitoso
```

Los errores se definen como stderr o un 2
```
whoam 2>/dev/null      #No me muestra los errores por pantalla

cat /etc/passwd &>/dev/null  #Redirige el stdout y el stderr al /dev/null por lo que no muestra nada en pantalla


disown      #Combierte un proceso en padre y no depende de otro

```

No utilizar demasiado 
```
sudo apt autoremove
```

Porque puede desinstalar mas cosas de la cuenta en cambio simula para ver que va a desinstalar
```
sudo apt autoremove --dry-run
```

Y recomendable desinstalar con 
```
apt remove nombre_paquete
```