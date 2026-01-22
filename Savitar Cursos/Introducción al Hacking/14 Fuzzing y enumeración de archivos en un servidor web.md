- Tags : #fuzzing #wfuzz #gobuster #ffuf #recursos_github #reverse_shell 
A continuación, te proporcionamos el enlace a estas herramientas:

- **Wfuzz**: [https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)
- **Gobuster**: [https://github.com/OJ/gobuster](https://github.com/OJ/gobuster)

**Wfuzz** es una herramienta de descubrimiento de contenido y una herramienta de inyección de datos. Básicamente, se utiliza para automatizar los procesos de prueba de vulnerabilidades en aplicaciones web.

Permite realizar ataques de fuerza bruta en parámetros y directorios de una aplicación web para identificar recursos existentes. Una de las **ventajas** de Wfuzz es que es altamente personalizable y se puede ajustar a diferentes necesidades de pruebas. Algunas de las **desventajas** de Wfuzz incluyen la necesidad de comprender la sintaxis de sus comandos y que puede ser más lenta en comparación con otras herramientas de descubrimiento de contenido.

Por otro lado, **Gobuster** es una herramienta de descubrimiento de contenido que también se utiliza para buscar archivos y directorios ocultos en una aplicación web. Al igual que Wfuzz, Gobuster se basa en ataques de fuerza bruta para encontrar archivos y directorios ocultos. Una de las principales **ventajas** de Gobuster es su velocidad, ya que es conocida por ser una de las herramientas de descubrimiento de contenido más rápidas. También es fácil de usar y su sintaxis es simple. Sin embargo, una **desventaja** de Gobuster es que puede no ser tan personalizable como Wfuzz.

Gobuster
```bash
gobuster dir -u https://wiffi.com -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 200

Excluir codigos de esado
gobuster dir -u https://wiffi.com -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 200 -b 403,404

Fuzzing a nivel de extensiones
gobuster dir -u https://wiffi.com -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 50 -b 403,404 -x php,html,txt

Con parametro -s para obtener solo status 200
gobuster dir -u https://wiffi.com -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 50 -x html -s 200 -b ''


```

Wfuzz
```bash
wfuzz -c -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ

Ocultar status code
wfuzz -c --hc=404,403 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ

Seguir la redireccion 
wfuzz -c --hc=404,403 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ/

Que devuelva rutas con una determinada cantidad de lineas -sl(show line) o -hl (hide line) lo mismo a nivel de palabras -hw o -sw y caracteres -hh -sh
wfuzz -c -sl=216 --hc=404,403 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ/

Para identificar extenciones ej html concatenamo al fuzz .html
wfuzz -c --hc=404,403 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ.html

Provar varias extenciones
wfuzz -c --hc=404,403 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -z list,html-txt-php -u https://wiffi.com/FUZZ.FUZ2Z

Aqui ocurre que para ir fuzzeando en diferentes partes de comando y con diferentes payload debemos ir agregando payload y por cada uno sera su numero de fuzz eje con -z list,html-txt-php creamos una lista que contiene 3 elementos html, txt , php resaltar que en wfuzz se declara como esta  en el comando y para agregar este payload al comando ponemos FUZ2Z en la posicion donde queremos sustituir los valores html, txt , php si creasemos otra lista o utlizaramos otro deccionario debemos sustituirlo poniedo FUZ3Z y asi sucesivamente

Para englobar rangos
wfuzz -c -z range,1-200000 -t 200 -u https://wiffi.com/detail?poruct=FUZZ
 
```

FFUF
```
ffuf -c -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ -v

Filtrar por codigo de estado
ffuf -c -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://wiffi.com/FUZZ -v --mc=200
```

Herramienta Web
https://phonebook.cz/