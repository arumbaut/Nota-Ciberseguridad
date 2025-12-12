```
echo; echo "0016
CABE
19C8
B2EC
A7CE
B39A
E7FA
EB90" | sort -u | while read line; do echo "[+] Puerto $line -> $(echo "obase=10; ibase=16; $line" | bc) - OPEN" ; done
```

Para ver que sericio esta corriendo por un puerto
```
lsoft -i:puerto
```