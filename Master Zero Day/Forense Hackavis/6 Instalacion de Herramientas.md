- Tags: #forense 


En linux especificamente en la distribucion SAND SIFT instalaremos 

```bash
#guymager
sudo apt install guymager

#Comando dd mejorado , un dd con exteroides
sudo apt install dcfldd  

#En esta distro ya esta instalado volatility pero instalaremos la version 3
mkdir Volatility3
cd Volatility3
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3/
pip3 install -r requirements
sudo mv volatility3 /opt
sudo ln -s /opt/volatility3/vol.py /usr/local/bin/vol3.py

#Ejecutar 
vol3.py 
```


*Links de la clase*:
[https://search.brave.com/search?q=sans+forensics](https://search.brave.com/search?q=sans+forensics)

[https://cyberdefenders.org/blueteam-ctf-challenges/africanfalls/](https://cyberdefenders.org/blueteam-ctf-challenges/africanfalls/)

[https://go.exterro.com/download-ftk-imager-82](https://go.exterro.com/download-ftk-imager-82)
