- Tags : #window #enumeration_windows #rdp #tools #recursos #recursos_tryhackme  #tool_xfreerdp #net_user #cmd_windows

**Recurso**: Maquina Investigating Windows TryHackme

*xfreerdp* : Es una herramienta para hacer conexiones RDP a maquinas window. Para utilizarla es necesario previamente tener usuario y pass de un objetivo.

```bash
xfreerdp /u:ususaro /p:password /v:ip_victima:port_donde_corre_rdp

#port_donde_corre_rdp : por defecto 3389 pero se puede cambiar, tener en cuenta. 
```

Enumeración de usuarios en un cmd de windows.

```bash
net user  #Enumera los usuarios del sitema

net user John   #Muestra info del usuario especificado

net localgroup  #Enumera los grupos del sistema

nel localgroup Administrator #Muestra info del grupo especificado
```