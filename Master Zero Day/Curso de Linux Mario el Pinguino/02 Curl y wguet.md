Parametro -o para establecer la salida del comando

```
curl https://www.aahsflhsd.com/loquesea.sh -o nombre.sh 
```

Para ver si una petición fue exitosa o no
```
curl -s -o /dev/null -w "{%http_code}\n" https://www.aahsflhsd.com/loquesea.sh -o nombre.sh
```

Wguet
-O para nombrar la salida
```
wguet https://www.aahsflhsd.com/loquesea.sh 

wguet -O scrip.sh https://www.aahsflhsd.com/loquesea.sh 

Descarga varios archivos
wguet https://www.aahsflhsd.com/loquesea.sh https://www.aahsflhsd.com/loquesea2.sh  

Descarga recursiva 
wguet -r https://www.aahsflhsd.com/loquesea/
```