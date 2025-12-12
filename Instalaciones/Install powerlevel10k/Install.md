Nos vamos al repo  https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#manual

Lanzamos este comando par cada usuario que queremos que la utilice
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc

Ejecutamos zsh para que nos ponga el menu de configuracion
del entorno de la powerlevel10k

```

El archivo de configuracion se encuentra en 
```
Aqui se hacen las modificaciones que querramos
/home/user/.p10k.zsh

Buscamos en el archivo 
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS

Agregamos tanto para el admin como el usurio normal
Cabe destacar que el proceso de instalacion se realiza para cada usuario 
context
command_execution_time
status

En la parte POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS comentaremos todo pues no queremos elementos en la derecha

y para el usuario root cuyo archivo se encuentra /root/.p10k.zsh 
ademas buscaremos ROOT_TEMPLATEy modificaremos 

typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE='%B%n@%m' #cambia a
typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE=''  #icon de nerd font

typeset -g POWERLEVEL9K_CONTEXT_PREFIX='%248Fwith '   #cambia a
typeset -g POWERLEVEL9K_CONTEXT_PREFIX=''

Esto al estar con el user root nos pone el icono seleccionado para idenificarlos
```