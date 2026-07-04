---
title: "Hack The Box Academy"
source: "https://academy.hackthebox.com/app/module/77/section/847"
author:
published:
created: 2026-05-21
description:
tags:
  - "clippings"
---
## Herramientas básicas

---

Herramientas como `SSH`, `Netcat`, `Tmux`, y `Vim` son esenciales y son utilizados diariamente por la mayoría de los profesionales de la seguridad de la información. Aunque estas herramientas no están destinadas a ser herramientas de prueba de penetración, son fundamentales para el proceso de prueba de penetración, por lo que debemos dominarlas.

---

## Usando SSH

[Carcasa segura (SSH)](https://en.wikipedia.org/wiki/SSH_\(Secure_Shell\)) es un protocolo de red que se ejecuta en el puerto `22` de forma predeterminada y proporciona a los usuarios, como los administradores de sistemas, una forma segura de acceder a una computadora de forma remota. SSH se puede configurar con autenticación de contraseña o sin contraseña usando [autenticación de clave pública](https://serverpilot.io/docs/how-to-use-ssh-public-key-authentication/) utilizando un par de claves públicas/privadas SSH. SSH se puede utilizar para acceder de forma remota a sistemas en la misma red, a través de Internet, facilitar conexiones a recursos en otras redes mediante reenvío/proxy de puertos y cargar/descargar archivos hacia y desde sistemas remotos.

SSH utiliza un modelo cliente-servidor, conectando a un usuario que ejecuta una aplicación cliente SSH como `OpenSSH` a un servidor SSH. Al atacar una caja o durante una evaluación del mundo real, a menudo obtenemos credenciales de texto sin cifrar o una clave privada SSH que podemos aprovechar para conectarnos directamente a un sistema a través de SSH. Una conexión SSH suele ser mucho más estable que una conexión de shell inversa y, a menudo, se puede utilizar como un "host de salto" para enumerar y atacar a otros hosts de la red, transferir herramientas, configurar la persistencia, etc. Si obtenemos un conjunto de credenciales, podemos utilizar SSH para iniciar sesión de forma remota en el servidor utilizando el nombre de usuario `@` la IP del servidor remoto, de la siguiente manera:

```
shellsessionaalonso1190@htb[/htb]$ ssh Bob@10.10.10.10

Bob@remotehost's password: *********

Bob@remotehost#
```

También es posible leer claves privadas locales en un sistema comprometido o agregar nuestra clave pública para obtener acceso SSH a un usuario específico, como analizaremos en una sección posterior. Como podemos ver, SSH es una excelente herramienta para conectarse de forma segura a una máquina remota. También proporciona una forma de mapear puertos locales en la máquina remota a nuestro host local, lo que a veces puede resultar útil.

---

## Usando Netcat

[Netcat](https://linux.die.net/man/1/nc), `ncat`, o `nc`, es una excelente utilidad de red para interactuar con puertos TCP/UDP. Se puede utilizar para muchas cosas durante un pentest. Su uso principal es para conectarse a shells, que analizaremos más adelante en este módulo. Además de eso, `netcat` se puede utilizar para conectarse a cualquier puerto de escucha e interactuar con el servicio que se ejecuta en ese puerto. Por ejemplo, `SSH` está programado para manejar conexiones a través del puerto 22 para enviar todos los datos y claves. Podemos conectarnos al puerto TCP 22 con `netcat`:

```
shellsessionaalonso1190@htb[/htb]$ netcat 10.10.10.10 22

SSH-2.0-OpenSSH_8.4p1 Debian-3
```

Como podemos ver, el puerto 22 nos envió su banner, indicando que `SSH` se está ejecutando en él. Esta técnica se llama `Banner Grabbing`, y puede ayudar a identificar qué servicio se está ejecutando en un puerto en particular. `Netcat` viene preinstalado en la mayoría de las distribuciones de Linux. También podemos descargar una copia para máquinas Windows desde aquí [link](https://nmap.org/download.html). Hay otra alternativa de Windows a `netcat` codificado en PowerShell llamado [Gato de poder](https://github.com/besimorhino/powercat). `Netcat` También se puede utilizar para transferir archivos entre máquinas, como analizaremos más adelante.

Otra utilidad de red similar es [socat](https://linux.die.net/man/1/socat), que tiene algunas características que `netcat` no es compatible, como reenviar puertos y conectarse a dispositivos seriales. `Socat` También se puede utilizar para [actualice un shell a un TTY totalmente interactivo](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/#method-2-using-socat). Veremos algunos ejemplos de esto en una sección posterior. `Socat` es una utilidad muy útil que debería formar parte del conjunto de herramientas de todo probador de penetración. A [binario independiente](https://github.com/andrew-d/static-binaries) de `Socat` se puede transferir a un sistema después de obtener la ejecución remota de código para obtener una conexión de shell inversa más estable.

---

## Usando Tmux

Terminal multiplexers, like `tmux` or `Screen`, are great utilities for expanding a standard Linux terminal's features, like having multiple windows within one terminal and jumping between them. Let's see some examples of using `tmux`, which is the more common of the two. If `tmux` is not present on our Linux system, we can install it with the following command:

```
shellsessionaalonso1190@htb[/htb]$ sudo apt install tmux -y
```

Once we have `tmux`, we can start it by entering `tmux` as our command: ![Terminal Parrot con mensaje de usuario que muestra el comando 'tmux'.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/getting_started_tmux_1.jpg)

The default key to input `tmux` commands prefix is `[CTRL + B]`. In order to open a new window in `tmux`, we can hit the prefix 'i.e. `[CTRL + B]` ' and then hit `C`: ![Terminal Parrot con mensaje de usuario listo para ingresar.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/getting_started_tmux_2.jpg)

We see the numbered windows at the bottom. We can switch to each window by hitting the prefix and then inputting the window number, like `0` or `1`. We can also split a window vertically into panes by hitting the prefix and then `[SHIFT + %]`: ![Terminal Parrot con dos paneles, cada uno de los cuales muestra indicaciones del usuario listas para ingresar.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/getting_started_tmux_3.jpg)

We can also split into horizontal panes by hitting the prefix and then `[SHIFT + "]`:

We can switch between panes by hitting the prefix and then the `left` or `right` arrows for horizontal switching or the `up` or `down` arrows for vertical switching. The commands above cover some basic `tmux` usage. It is a powerful tool and can be used for many things, including logging, which is very important during any technical engagement. This [cheatsheet](https://tmuxcheatsheet.com/) is a very handy reference. Also, this [Introduction to tmux](https://www.youtube.com/watch?v=Lqehvpe_djs) video by `ippsec` is worth your time.

---

## Using Vim

[Vim](https://linuxcommand.org/lc3_man_pages/vim1.html) is a great text editor that can be used for writing code or editing text files on Linux systems. One of the great benefits of using `Vim` is that it relies entirely on the keyboard, so you do not have to use the mouse, which (once we get the hold of it) will significantly increase your productivity and efficiency in writing/editing code. We usually find `Vim` or `Vi` installed on compromised Linux systems, so learning how to use it allows us to edit files even on remote systems. `Vim` also has many other features, like extensions and plugins, which can significantly extend its usage and make for a great code editor. Let's see some of the basics of `Vim`. To open a file with `Vim`, we can add the file name after it:

```
shellsessionaalonso1190@htb[/htb]$ vim /etc/hosts
```

![Parrot Terminal muestra un archivo de configuración con configuraciones de red y comentarios.](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/77/getting_started_vim_1.jpg)

If we want to create a new file, input the new file name, and `Vim` will open a new window with that file. Once we open a file, we are in read-only `normal mode`, which allows us to navigate and read the file. To edit the file, we hit `i` to enter `insert mode`, shown by the " `-- INSERT --` " at the bottom of `Vim`. Afterward, we can move the text cursor and edit the file:

Once we are finished editing a file, we can hit the escape key `esc` to get out of `insert mode`, back into `normal mode`. When we are in `normal mode`, we can use the following keys to perform some useful shortcuts:

| Command | Description |
| --- | --- |
| `x` | Cut character |
| `dw` | Cut word |
| `dd` | Cut full line |
| `yw` | Copy word |
| `yy` | Copy full line |
| `p` | Paste |

Tip: We can multiply any command to run multiple times by adding a number before it. For example, '4yw' would copy 4 words instead of one, and so on.

If we want to save a file or quit `Vim`, we have to press`:` to go into `command mode`. Once we do, we will see any commands we type at the bottom of the vim window:

There are many commands available to us. The following are some of them:

| Command | Description |
| --- | --- |
| `:1` | Go to line number 1. |
| `:w` | Write the file, save |
| `:q` | Quit |
| `:q!` | Quit without saving |
| `:wq` | Write and quit |

`Vim` is a very powerful tool and has many other commands and features. This [cheatsheet](https://vimsheet.com/) is an excellent resource for further unlocking the power of `Vim`.

