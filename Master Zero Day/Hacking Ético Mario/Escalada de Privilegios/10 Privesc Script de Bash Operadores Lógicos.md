- Tags : #recursos #recursos_dockerlabs #escalada #escalada_privilegios 

**Recursos**: Maquina BruteShock dockerlabs.es

Cuando tenemos una script que se le pasan valores y evalua este de la forma `[[ $val -eq expresion]]`  podemos ser capaces de injectar codigo en la entrada de de datos del tipos

```bash
a[$(/bin/bash >&2)]+42
```

# ⭐ El script que tienes

```
#!/bin/bash  
read -rp "Adivina: " num  
if [[ $num -eq 123123 ]] then   
	echo "Si" 
else   
	echo "ERROR" 
fi
```

---

# ⭐ Paso 1 — Qué hace `read`

`read -rp "Adivina: " num`

👉 Guarda lo que escribes en la variable `num`.

Si introduces:

`a[$(/bin/bash >&2)]+42`

Entonces:

`num = a[$(/bin/bash >&2)]+42`

Hasta aquí solo es texto.

---

# ⭐ Paso 2 — Aquí está la clave real

La línea peligrosa es:

`[[ $num -eq 123123 ]]`

---

# ⭐ Qué significa `-eq`

`-eq` es un operador de comparación **numérica**.

Bash intenta evaluar:

👉 `$num` como expresión matemática.

---

# ⭐ Punto CRÍTICO (el bug)

Cuando Bash evalúa expresiones numéricas dentro de `[[ ]]`, permite:

👉 Evaluación aritmética  
👉 Expansión de arrays  
👉 Expansión de comandos

Y aquí ocurre la magia.

---

# ⭐ Qué significa la entrada

`a[$(/bin/bash >&2)]+42`

Vamos parte por parte.

---

# ⭐ Parte 1 — `$(...)`

Esto es **command substitution**.

Significa:

👉 Ejecuta el comando dentro  
👉 Sustituye el resultado

---

Entonces:

`$(/bin/bash >&2)`

Hace:

👉 Ejecuta bash  
👉 Redirige salida a stderr

---

⚠️ La redirección `>&2` se usa para que el comando no interfiera con la evaluación normal.

---

# ⭐ Parte 2 — `a[...]`

Esto parece acceso a array.

En Bash:

`array[indice]`

Pero Bash evalúa primero el índice.

---

Entonces:

`a[$(/bin/bash >&2)]`

Significa:

👉 Ejecuta lo que hay dentro de `[]`  
👉 Antes de evaluar el array

---

# ⭐ Por qué Bash ejecuta el comando

Porque en evaluaciones aritméticas Bash permite:

`array[$(comando)]`

Y ejecuta el comando para calcular el índice.

---

# ⭐ Parte 3 — `+42`

Esto es simplemente para que la expresión parezca numérica.

Bash intenta resolver:

`algo + 42`

Aunque falle luego, el comando ya se ejecutó.

---

# ⭐ Flujo real que ocurre

Cuando el script evalúa:

`[[ $num -eq 123123 ]]`

Bash hace:

1. Interpreta `$num` como expresión aritmética
    
2. Detecta `a[...]`
    
3. Evalúa el índice del array
    
4. Ejecuta `$(/bin/bash >&2)`
    
5. Se lanza una shell
    

---

# ⭐ Lo importante

👉 El comando se ejecuta durante la evaluación  
👉 No importa si la comparación falla después

---

# ⭐ Por qué pasa esto

Porque Bash permite:

`Arithmetic Expansion`

Dentro de comparaciones numéricas.

---

# ⭐ Cómo puedes comprobar este comportamiento

Si pruebas en Bash:

`echo $(( a[$(id)] ))`

Verás que ejecuta el comando dentro.

---

# ⭐ Esto NO ocurre con comparaciones de texto

Si el script usara:

`[[ "$num" == "123123" ]]`

👉 No habría evaluación aritmética  
👉 No se ejecutaría nada

---

# ⭐ Por qué esto es una vulnerabilidad real

Porque:

👉 El script confía en input del usuario  
👉 Lo usa en comparación numérica  
👉 Bash evalúa expresiones dinámicamente

---

# ⭐ Cómo arreglar el script (visión defensiva)

Validar que sea número antes:

`if [[ "$num" =~ ^[0-9]+$ ]]`

Luego comparar.

---

# ⭐ Resumen sencillo

La bash se ejecuta porque:

👉 `-eq` obliga a Bash a evaluar `$num` como expresión matemática  
👉 Bash permite ejecutar comandos dentro de expresiones aritméticas  
👉 Tu entrada usa `$(...)` que ejecuta comandos  
👉 Bash ejecuta eso mientras intenta calcular el valor

---

# ⭐ Concepto clave que debes recordar (nivel OSCP / eJPT)

`Comparaciones numéricas en Bash pueden ejecutar código si no validas input.`