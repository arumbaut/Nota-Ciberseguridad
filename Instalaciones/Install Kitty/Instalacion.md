Nos descargamos la Kitty del repo
https://github.com/kovidgoyal/kitty/releases

El archivo **Linux amd64 binary bundle**  este es el que trabaja correctamente.
```
Copianmos el archivo descargado a /opt/kitty

7z x archivo   #descomprimimos
tar -xv archivo tar #descomprimimos el archivo tar


En la carpeta /home/usuario/.config/kitty copiamos los archivos de configuracion de savitar  color.ini y kitty.conf


```

color.ini
```
cursor_shape          Underline
cursor_underline_thickness 1
window_padding_width  20

# Special
foreground #a9b1d6
background #1a1b26

# Black
color0 #414868
color8 #414868

# Red
color1 #f7768e
color9 #f7768e

# Green
color2  #73daca
color10 #73daca

# Yellow
color3  #e0af68
color11 #e0af68

# Blue
color4  #7aa2f7
color12 #7aa2f7

# Magenta
color5  #bb9af7
color13 #bb9af7

# Cyan
color6  #7dcfff
color14 #7dcfff

# White
color7  #c0caf5
color15 #c0caf5

# Cursor
cursor #c0caf5
cursor_text_color #1a1b26

# Selection highlight
selection_foreground #7aa2f7
selection_background #28344a
```

kitty.conf
```
enable_audio_bell no

include color.ini

font_family HackNerdFont
font_size 13

disable_ligatures never

url_color #61afef

url_style curly

map ctrl+left neighboring_window left
map ctrl+right neighboring_window right
map ctrl+up neighboring_window up
map ctrl+down neighboring_window down

map f1 copy_to_buffer a
map f2 paste_from_buffer a
map f3 copy_to_buffer b
map f4 paste_from_buffer b

cursor_shape beam
cursor_beam_thickness 1.8

mouse_hide_wait 3.0
detect_urls yes

repaint_delay 10
input_delay 3
sync_to_monitor yes

map ctrl+shift+z toggle_layout stack
tab_bar_style powerline

inactive_tab_background #e06c75
active_tab_background #98c379
inactive_tab_foreground #000000
tab_bar_margin_color black

map ctrl+shift+enter new_window_with_cwd
map ctrl+shift+t new_tab_with_cwd

background_opacity 0.95

shell zsh
```

Instalamos la zsh 
```
sudo apt install zsh

usermod -s zsh usuario  #para root y para el usurio comun
```

Ponemos para los dos usuario como terminal por defecto la kitty
```
Primero 
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/local/bin/kitty 50

Usuario normal

sudo update-alternatives --config x-terminal-emulator

Para sudo
sudo su

update-alternatives --config x-terminal-emulator
```

Agregamos el tipo de letra que vamos a utilizar en la terminal, la descargamos de https://www.nerdfonts.com/font-downloads
Hack Nerd Font y descomprimimos el contenido en /usr/local/share/fonts
Actualizar las letras del sistema
```
sudo fc-cache -f -v
```
Finalmente reiniciamos la terminal y listo.
