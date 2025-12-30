Instalar aplicaciones con flatpak

```
Isntall flatpak
sudo apt install flatpak

## Añadir el repositorio Flathub
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

Instalar aplicacion de los repos de flathub
flatpak install flathub com.obsproject.Studio

Desinstalar aplicacion
flatpak uninstall obsproject 

Limpiar completamente lo que ya no se este utilizando 
flatpak uninstall --unused
```