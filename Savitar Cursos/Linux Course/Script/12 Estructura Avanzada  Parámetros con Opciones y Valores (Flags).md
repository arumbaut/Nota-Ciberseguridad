## Estructura Avanzada: Parámetros con Opciones y Valores (Flags)

En el mundo real, los scripts y comandos complejos usan **opciones** o **banderas** (flags), como `-f` o `--file`, seguidas de un valor.

Para manejar este tipo de argumentos, se utiliza el comando interno de Bash llamado **`getopts`** (para opciones cortas) o bibliotecas externas (para opciones largas como `--file`).

### Ejemplo con `getopts` (Opciones Cortas)

Este script usa un bucle `while` y `getopts` para buscar las opciones `-f` (archivo) y `-t` (tipo):

```
#!/bin/bash

ARCHIVO=""
TIPO="default"

# El bucle 'getopts' procesa las opciones una por una.
# 'f:' espera un valor después de -f (por eso lleva ':')
# 't:' espera un valor después de -t

while getopts "f:t:" opcion; do
    case "${opcion}" in
        f)
            ARCHIVO=${OPTARG}
            ;;
        t)
            TIPO=${OPTARG}
            ;;
        *)
            echo "Uso: $0 [-f <archivo>] [-t <tipo>]"
            exit 1
            ;;
    esac
done

# 'shift' descarta las opciones ya procesadas por getopts
# y deja el resto de argumentos posicionales disponibles (si los hay)
shift $((OPTIND-1))

echo "-----------------------------------"
echo "Archivo a procesar: $ARCHIVO"
echo "Tipo de procesamiento: $TIPO"
echo "Argumentos posicionales restantes: $@"
```