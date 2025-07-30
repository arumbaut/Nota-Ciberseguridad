
Paso 1: Instalar GVM

```
sudo apt update
sudo apt install gvm

```

### ✅ Paso 2: Configurar GVM

Después de instalar, debes ejecutar el siguiente comando para configurar y actualizar el sistema:

```
sudo gvm-setup
```

### ✅ Paso 3: Verificar el estado

```
sudo gvm-check-setup
```

### ✅ Paso 4: Iniciar GVM

```
sudo gvm-start
```

### ✅ Paso 5: Acceder a la interfaz web

Una vez iniciado, verás un mensaje similar a este:

```
Web interface (Greenbone Security Assistant) is running at: https://127.0.0.1:9392
```

## 🔒 Usuario y contraseña por defecto

Si no viste el usuario/contraseña, puedes regenerarlo así:

```
sudo gvm-manage-certs -a   # generar nuevos certificados sudo gvmd --create-user kali sudo gvmd --user= kali --new-password= tu_contraseña
```

## ¿No sabes el usuario o contraseña?

Puedes ver los usuarios existentes con:

```
sudo gvmd --get-users
```

Si necesitas crear uno nuevo:

```
sudo gvmd --create-user tu_usuario sudo gvmd --user=tu_usuario --new-password=tu_contraseña
```