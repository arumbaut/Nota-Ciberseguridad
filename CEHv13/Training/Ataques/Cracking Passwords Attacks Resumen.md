|**Bloque**|**Técnicas y ataques**|
|---|---|
|**I. Non-Electrónicos**|Social Engineering, Shoulder Surfing, Dumpster Diving|
|**II. Activos Online**|Dictionary, Brute-Force, Password Spraying, Mask, Rule-based, Hybrid, Syllable, Hash Injection/PtH, LLMNR/NBT-NS Poisoning, Trojans/Spyware/Keyloggers, Internal Monologue, Kerberoasting, AS-REP Roasting, NTLM Relay|
|**III. Pasivos Online**|Wire Sniffing, MITM/Manipulator-in-the-Middle, Replay Attacks|
|**IV. Offline**|Rainbow Tables, Distributed Network Attack|
|**V. Kerberos & Tickets**|Pass-the-Ticket (Silver/Golden), NTLM Relay (Responder), Mimikatz/Rubeus/etc.|

---

## 2. Resumen y **puntos clave** por bloque

### Bloque I: Non-Electrónicos

- **Social Engineering**: explota confianza/psicología para sonsacar credenciales.
    
- **Shoulder Surfing**: observa físicamente pantallas o teclados.
    
- **Dumpster Diving**: rebusca en la basura documentos con datos sensibles.
    

### Bloque II: Activos Online

- **Dictionary Attack**: prueba palabras comunes de un listado.
    
- **Brute-Force**: explora todas las combinaciones posibles (John the Ripper).
    
- **Rule-based**: diccionario + reglas (conocimiento de patrones).
    
- **Mask Attack**: define máscara de caracteres (e.g. “?l?l?d?d”).
    
- **Hybrid Attack**: diccionario + sufijos/prefijos.
    
- **Syllable Attack**: combina sílabas para generar posibles contraseñas.
    
- **Password Spraying**: pocas contraseñas populares probadas en muchas cuentas (thc-hydra).
    
- **Hash Injection / Pass-the-Hash**: inyecta hash NTLM/LM para autenticarse sin saber la contraseña.
    
- **LLMNR/NBT-NS Poisoning**: responde a consultas de nombre en LAN para capturar hashes.
    
- **Trojans/Spyware/Keyloggers**: instala malware para robar datos o registrar pulsaciones.
    
- **Internal Monologue**: usa SSPI para generar NetNTLM internamente.
    
- **Kerberoasting**: extrae y descifra tickets TGS cifrados con hash de servicio.
    
- **AS-REP Roasting**: explota cuentas sin preautenticación para robar el TGT y descifrarlo.
    
- **NTLM Relay**: intercepta y retransmite autenticaciones NTLM (Herramienta: Responder).
    

### Bloque III: Pasivos Online

- **Wire Sniffing**: captura paquetes en tránsito para extraer credenciales.
    
- **MITM / Manipulator-in-the-Middle**: intercepta y puede modificar la comunicación.
    
- **Replay Attacks**: reenvía mensajes legítimos capturados para re-ejecutar acciones autorizadas.
    

### Bloque IV: Offline

- **Rainbow Table Attack**: precalcula tablas hash→contraseña para descifrado rápido.
    
- **Distributed Network Attack**: reparte la tarea de crackeo en múltiples máquinas (DNA).
    

### Bloque V: Kerberos & Tickets

- **Pass-the-Ticket**: reutiliza TGT o ST capturados para autenticarse (Silver vs Golden Tickets).
    
- **Golden Ticket**: hash KRBTGT permite generar TGT para cualquier usuario.
    
- **Silver Ticket**: tickets para servicios específicos.
    
- **Herramientas clave**: Mimikatz, Rubeus, Windows Credentials Editor.