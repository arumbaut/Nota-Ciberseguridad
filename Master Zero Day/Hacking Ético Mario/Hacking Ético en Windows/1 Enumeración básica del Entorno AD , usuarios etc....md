- Tags : #ad_enumeracion #recursos #recursos_tryhackme  #tools #tools_enum4linux #kerbrute #enumeration #enumeration_windows #window 

**Recurso**: Maquina Attacktive Directory tryhackme
**Herramienta**: *enum4linux* viene con kali

Enumeración Basica
```bash
enum4linux nombre_dominio

enum4linux spookysec.local
```

Valido destacar que no es infalible esta herramienta pero si es un buen punto de partida. Es mucho mas efectiva cuando ya tenemos comprometido un usuario del dominio.

Enumeración de Usuarios
**Herramienta**: *Kerbrute*  [https://github.com/TarlogicSecurity/kerbrute](https://github.com/TarlogicSecurity/kerbrute)

Para la enumeración de usuarios con Kerbrute es necesario una lista de usuarios y otra de passwords para ejecutar el ataque para identificar a los usuarios de dominio

```bash
python3 kerbrute.py -users userlist.txt -password passwordlist.txt -domain spookysec.local -t 100 
```

![](../../../attachments/Pasted%20image%2020260212094848.png)

Otra opción: *kerberus-enum *  [https://github.com/Maalfer/kerberos-enum](https://github.com/Maalfer/kerberos-enum)

```bash
bash kerbrute-enum.sh userlist.txt spookysec.local
```