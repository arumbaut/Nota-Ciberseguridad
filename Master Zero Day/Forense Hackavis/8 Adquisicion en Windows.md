- Tags : #forense #adquisicion_windows #adquisicion_windows_memoria

Estructura de carpetas de una Adquisición 
`Adquisiciones/Memoria RAM/Evidencias/001

*FTK IMAGER*

![](../../../attachments/Pasted%20image%2020260309115848.png)

![](../../../attachments/Pasted%20image%2020260309121309.png)

Comporobar la integridad de la evidencia 

```powershell
ls

Get-FileHash -Path .\Memoria_RAM_Windows10x64.raw -Algorithm MD5
```