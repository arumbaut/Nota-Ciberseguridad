- Tags: #fuzzing #wordlist #gobuster 

```bash
dirb http://127.0.0.1/

gobuster dir -u http://127.0.0.1:8080/ -w /usr/share/seclist/Discovery/Web-Content/dyrectory-list-lowercase-2.3-medium.txt -x php,txt,back
```