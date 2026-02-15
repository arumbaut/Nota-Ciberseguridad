- Tags : #wffuz #enumeration_subdominios #dict_subdominos #tools_online #tools  

```bash

wffuz -c --hc=404 --hl=1 -w /usr/share/seclist/Discovery/DNS/Subdoamins-top1million-20000.txt -H "Host: FUZZ.doamin.es" -u ip_objetivo
```

**subfinder**
```bash
subfinder -d dockerlabs.es
```

**Sublister**
```bash
sublister -d dockerlabs.es
```

**DnsRecond**
```bash
dnsrecond -d dockerlabs.es -t brt -D /usr/share/seclist/Discovery/DNS/Subdoamins-top1million-20000.txt 

-t brt #Indica ataque de FBruta
-D /dir #Indica wordlist a utilizar para la FB
```

**Enumeración de subdominios con dnsdumpster_supr**
**Recurso** : [https://dnsdumpster.com/](https://dnsdumpster.com/)
