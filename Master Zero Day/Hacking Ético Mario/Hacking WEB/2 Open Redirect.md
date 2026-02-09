- Tags: #recursos #recursos_github #open_redirect  #tools #oralyzer

**Recursos**: [https://gist.github.com/0xblackbird/d7677a05ea50586cf2be0a601e665d1a](https://gist.github.com/0xblackbird/d7677a05ea50586cf2be0a601e665d1a)
[https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Open%20Redirect/README.md](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Open%20Redirect/README.md)

Es cuando podemos manipular los hipervínculos de las paginas webs para enviarlo a una pagina maliciosa.
En ocaciones pueden haber validaciones que nos impidan la redirección pero hay formas de vaipasearlas

```Ejemplo

Concatenamos la url maliciosa con un arroba

http://172.17.0.2/ejemplo3/redirect.php?url=https://www.google.com@url_maliciosa


Tambien se debe revisar si nos permite redirigira a subdominios

http://172.17.0.2/ejemplo3/redirect.php?url=https://www.test.google.com
```


Open Redirect Automatico con Oralyzer
**Tool**: [https://github.com/r0075h3ll/Oralyzer](https://github.com/r0075h3ll/Oralyzer)

```bash
sudo apt install python3-requests
sudo apt install python3-bs4
sudo apt install python3-urllib3

python3 oralyzer.py -u http://172.17.0.2/ejemplo3/redirect.php?url=https://www.test.google.com)
```

**Enumeración de rutas vulnerables y explotación con Oralyzer**

Lab vulnerable : [http://testphp.vulnweb.com/](http://testphp.vulnweb.com/)

**Tools**: ParamSpider 
[https://github.com/devanshbatham/ParamSpider](https://github.com/devanshbatham/ParamSpider)
```bash
git clone https://github.com/devanshbatham/ParamSpider

pip install .

paramspider -d testphp.vulnweb.com
```