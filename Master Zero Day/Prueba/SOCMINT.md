### 🔍 Paso 1 — Confirmar que es un ID de Twitter/X

Los IDs de Twitter son Snowflake IDs de 64 bits. El número `1797782924714004480` tiene 19 dígitos, lo que encaja perfectamente con ese formato.

---

### 🔍 Paso 2 — Convertir el ID a nombre de usuario

Tienes varias formas de hacerlo:

**Opción 1 — [Tweeterid.com** La herramienta más directa: 👉 **[https://tweeterid.com](https://tweeterid.com)**](https://www.mediamister.com/es/buscar-id-de-usuario-de-twitter) Pega el número `1797782924714004480` y te devuelve el @username.

**Opción 2 — API pública de Twitter (sin login)** Abre el navegador y ve a:

```
https://twitter.com/intent/user?user_id=1797782924714004480
```

Si la cuenta existe te redirige al perfil directamente.

**Opción 3 — Herramienta online alternativa** 👉 **[https://codeofaninja.com/tools/find-twitter-id/](https://codeofaninja.com/tools/find-twitter-id/)**

---

### 🔍 Paso 3 — Verificar el resultado

Una vez tengas el username, confirma que la cuenta existe buscando en:

```
https://twitter.com/[username]
```

o en X.com:

```
https://x.com/[username]
```

---

### 📄 Formato de la FLAG

Una vez encuentres el username:

```
FLAG{@nombreusuario}
```

Prueba con Tweeterid.com primero — es la opción más rápida y no necesitas cuenta. ¿Qué resultado te da?
FLAG{@jcbelezaw}

![[Pasted image 20260530155258.png]]

![[Pasted image 20260530230500.png]]

![[Pasted image 20260530232950.png]]

![[Pasted image 20260530233012.png]]

![[Pasted image 20260530233308.png]]