

*Nos vamos a la* `/home/alexandross/.config/nvim/lua/plugins/`
```bash
cd /home/alexandross/.config/nvim/lua/plugins/

#Cremos un file
nano /home/alexandross/.config/nvim/lua/plugins/copilot.lua

```

*Le agregamos esto y reiniciamos NVIM (lo abrimos y cerramos)*
```lua

local plugins = {
  {
    "github/copilot.vim",
    lazy = false, -- Queremos que cargue al inicio para tener sugerencias siempre
  },
}

return plugins
```

Dentro de NVIM se instaara el plugin y lugo hacemos `:Copilot setup` para que nos de un codigo para conectarno a nuestra cuenta de *github copilot*  [cuenta de github ]