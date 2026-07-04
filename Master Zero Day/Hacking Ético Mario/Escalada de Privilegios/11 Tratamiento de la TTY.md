- Tags: #tty #tratamiento_tty #recursos #recursos_dockerlabs 

**Recurso**: Maquina WorkingCMS dockerlabs

```bash
script /dev/null -c bash

Ctrl+Z

stty raw -echo; fg

reset xterm

export SHELL=bash
export TERM=xterm

stty rows 37 columns 145     
#Estos valores los tomamos de una ventana en nuestra terminal con un `stty size`


```