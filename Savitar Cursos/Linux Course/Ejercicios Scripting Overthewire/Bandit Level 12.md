Fichero en hexadecimal , para convertir a hexadecimal utilizamos el comando xxd

Pass next level : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

reverse de hexadecimal
```
cat data.txt | xxd -r > datos

Si quisieramos guardarlo en el mismo archivo utiliamos sponge

cat data | xxd -r | sponge data

Luego revisamos par ver que tipo de archivo es y lo vamos descomprimiendo por tipo de arvhivo si es un gz le ponemos la extencion y lo descomprimimos, si es bzip2 le ponemos .bz y lo descomprimimos si es tar lo mismo hasta que llegamos al txt 


```

Descompactador automático [[Script Descomprecion]] 