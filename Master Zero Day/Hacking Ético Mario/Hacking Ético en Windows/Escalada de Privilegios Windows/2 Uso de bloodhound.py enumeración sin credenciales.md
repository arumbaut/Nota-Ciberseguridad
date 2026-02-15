- Tags: #window #escalada #escalada_privilegios_windows #tool_bloodhound#enumeration #enumeration_windows #enumeration_active_directory #active_directory #recursos #recursos_vulnyx #tool_bloodhound_py #tool_bloodyAD

**Recurso**: Maquina Change Vulnyx
Enumerar *active directory* cuando no tenemos aun intrusion a la maquina pero si tenemos credenciales validas de un usuario del dominio. En estos casos utilizaremos la herramienta *bloodhoud.py* para la enumeración .

*github bloodhound.py*: [https://github.com/dirkjanm/BloodHound.py](https://github.com/dirkjanm/BloodHound.py)

```bash
#Para enumerar lo maximo posible del dominio
pyhon3 bloodhound.py -u 'alfredo' -p 'Pass123' -ns 172.19.122.92 -d megachange.nyx -c all --zip
```

Luego seria igual que en los casos anteriores, activamos *neo4j* y abrimos *bloodhoud* y le subimos el archivo que generamos con *bloodhound.py*  

![](../../../../attachments/Pasted%20image%2020260214064145.png)

Cuando veamos los privilegios o las capacidades que tenga nuestro usuario comprometido en *bloodhoud* es recomendable también hacer una búsqueda en internet de esto pues puede darse el caso que lo que nos sugiera bloodhound no funcione y no debemos detenernos si no buscar alternativas.

![](../../../../attachments/Pasted%20image%2020260214064742.png)

Buscamos en google privesc forcechangepassword
![](../../../../attachments/Pasted%20image%2020260214064909.png)

![](../../../../attachments/Pasted%20image%2020260214065055.png)

Probamos con  la herramienta *bloodyAD*

```bash
bloodyAD --host "10.210.177.183" -d "megachange.nyx" -u "alfredo" -p "Password1" set password "sysadmin" "Pingu123"
```