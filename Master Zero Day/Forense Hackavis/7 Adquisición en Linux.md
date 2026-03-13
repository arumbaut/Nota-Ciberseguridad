- Tags: #forense #adquisicion_linux #linux #adquisicion_linux_memoria #window 


### Lime : Herramienta de adquisicion de memoria
*Link*: [https://github.com/504ensicsLabs/LiME](https://github.com/504ensicsLabs/LiME)

```bash
git clone https://github.com/504ensicsLabs/LiME.git
cd LIME
cd src
make

sudo insmod ./lime*ko "path=tmp/memoria.lime format=lime"

#Enviamos a nuestra maquina para analizar el memoria.lime
nc 192.188.1.199 1234 < memoria.lime 

nc -nvlp 1234 | pv -b > memoria.lime

pv -b #Monitores la transferencia
```

![](../../../attachments/Pasted%20image%2020260309113644.png)

### AVML: Herramienta de adquisicion de memoria
*Link*: [https://github.com/microsoft/avml](https://github.com/microsoft/avml)
```bash
#Nos descargamos el binario 
wget https://github.com/microsoft/avml/releases/download/v0.17.0/avml

chmod +x avml
su ./avml
./avml memoria.raw
```

 *Volatility2* solo llego hasta la version del kernel *18.04* , a partir de esta hay que utilizar *Volatility3* 