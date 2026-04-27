[[4.HTTP Enumeration]]

```bash

whatweb ip

```

#### Nmap scrips

```bash

nmap ip -sV -p 80 --script http-enum

nmap ip -sV -p 80 --script http-headers

nmap ip -sV -p 80 --script http-methods --script-arguments http-methods.url-path=/webday/

nmap ip -sV -p 80 --script http-webdav-scan --script-arguments http-methods.url-path=/webday/
```

#### Para apache
```bash
nmap ip -sV -p 80 -script banner
```

#### Metasploit
```bash

mfsconsole
>use auxiliary/scanner/http_version
>set rhost ip
>options
>run

mfsconsole
>use auxiliary/scanner/http/robots_txt
>set rhost ip
>options
>run
```

#### Directory traverse

##### MFSCONSOLE
```bash
mfsconsole
>use auxiliary/scanner/http/brute_dirs
>set rhost ip
>options
>run
```

##### DIRB
```bash
dirb http://ip /usr/share/metasploit-framework/data/wordlists/directory.txt
```

