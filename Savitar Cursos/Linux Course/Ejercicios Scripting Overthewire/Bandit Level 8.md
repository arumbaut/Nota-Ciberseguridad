Buscar la linea que se repita una vez

Pass next level 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

```
sort data.txt | uniq -u

sort data.txt | uniq -c

sort data.txt | uniq -c | grep -w 1
```