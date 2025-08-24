Para hacer fuzzin de parametros mediante consola tambien se puede utilizar Burpsuit para esto


## 🔧 USO BÁSICO – FUZZEAR DIRECTORIOS

```
wfuzz -c -w /usr/share/wordlists/dirb/common.txt --hc 404 http://target.com/FUZZ
```

📌 **Explicación:**

- `-c` → Salida en color
    
- `-w` → Ruta del diccionario
    
- `--hc 404` → Oculta respuestas con código 404 (no encontradas)
    
- `FUZZ` → Lugar donde se sustituye el valor del diccionario
    

---

## 🔐 FUZZEAR FORMULARIOS DE LOGIN

```
wfuzz -c -w users.txt -w passwords.txt -d "username=FUZZ&password=FUZ2Z" --hc 401 http://target.com/login
```

📌 **Explicación:**

- `-d` → Petición POST con cuerpo
    
- `FUZZ` y `FUZ2Z` → Valores que Wfuzz va reemplazando
    
- `--hc 401` → Oculta los intentos con respuesta 401 (fallidos)
    

---

## 🛠️ PARÁMETROS ADICIONALES ÚTILES

- `--hh` → Ocultar respuestas según tamaño (útil cuando el código no cambia)
    
- `--hw` → Ocultar por número de palabras
    
- `--hs` → Ocultar por número de líneas
    
- `--hc` → Ocultar por código HTTP (ej. 404)
    
- `-X` → Método HTTP (GET, POST, etc.)
    
- `-H` → Encabezado personalizado (ej. cookies, user-agent)
    

---

## 🔍 EJEMPLO DE FUZZEO DE PARÁMETROS EN GET

bash

CopyEdit

`wfuzz -c -w params.txt --hc 404 "http://target.com/page.php?FUZZ=test"`

---

## 🧠 TIP: DICCIONARIOS

Puedes usar diccionarios de:

- `/usr/share/wordlists/`
    
- Diccionarios de **SecLists** (muy recomendados): [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)