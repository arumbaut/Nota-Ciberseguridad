## ==🧩 ¿Por qué se ve -script, --script, --script-http, --script http-enum?==

### ==1\. ✅ -script y --script son lo mismo==

- Ambos son **opciones válidas** en `nmap`, simplemente con forma corta y larga:
	No hay diferencia funcional entre `-script` y `--script`.

---

## 🎯 Ejemplo completo con argumentos

- `--script ssh-hostkey`: especifica el script a ejecutar.
- `--script-args ssh_hostkey=full`: pasa un argumento para que muestre todas las claves posibles.

---

## Ejemplo completo

Si estás usando `http-brute` y quieres ver qué argumentos puedes pasar:

```
nmap --script-help http-brute

```

Verás que puedes usar:
```
--script-args userdb=usuarios.txt,passdb=claves.txt
```

Puedes combinar varios scripts y sus argumentos en un solo comando:
```
nmap -p 80 \
  --script http-brute,http-title \
  --script-args userdb=usuarios.txt,passdb=claves.txt,http-useragent="Mozilla/5.0" \
  192.168.1.10

```