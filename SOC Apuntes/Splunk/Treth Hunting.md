
Ejemplo para detectar filtración de tat estableciendo un linea base
```
index=sample sourcetype=stream:http http_method=POST

| stats sum(bytes_out) as count by src_ip, dest_ip

| sort -count
```

Después de una evaluación inicial y la limpieza de nuestros datos, podemos calcular nuestro "resumen de cinco números", más la media y la desviación estándar, para obtener una descripción estadística de nuestra muestra... ¡todo dentro de Splunk!

```
index=sample sourcetype=stream:http http_method=POST

| stats sum(bytes_out) as count by src_ip, dest_ip  
| stats min(count) as min,  
 max(count) as max,  
 median(count) as median,  
 perc25(count) as Q1,  
 perc75(count) as Q3,  
 mean(count) as mean,  
 stdev(count) as stdev
```

Anteriormente aprendimos que el Rango Intercuartil (RIC) es la diferencia entre el primer (Q1) y el tercer (Q3) cuartil y representa, en cierto modo, el rango donde se encuentran la mayoría de los valores en un conjunto de datos.

Al buscar valores atípicos, buscamos valores alejados de este "centro", ya sea en dirección positiva o negativa. En nuestro ejemplo, buscamos un aumento anormal en los volúmenes de transferencia, por lo que buscaremos valores positivos o valores que se encuentren en el extremo superior.

Una forma común de hacerlo es buscar puntos de datos que sean mayores o iguales a 1,5 veces el RIC y alejados de la mediana.

Traduciendo esto a una fórmula, obtenemos:
**IQR outliers >= median + (1.5 * (Q3-Q1))**

```
index=sample sourcetype=stream:http http_method=POST

| stats sum(bytes_out) as count by src_ip, dest_ip  
| where count >= 120758  
| sort - count
```


Aprendimos que la desviación estándar (𝛔) es la distancia promedio entre la mediana y cada punto de datos. Nuevamente, buscamos puntos de datos que se alejen de la normalidad que representan estos valores.

Un enfoque común consiste en multiplicar la desviación estándar por un umbral y sumar la media para encontrar valores que destaquen, ya sea en sentido positivo o negativo, según lo que se busque. El umbral puede ser 2 o 3, según la sensibilidad deseada para las estimaciones.

Dado que nos centramos en la posible exfiltración de datos o en las comunicaciones de Comando y Control, nos centraremos nuevamente en los valores atípicos.
As a formula, this looks something like:

**standardDev_outliers >= mean + 3𝛔**

```
index=sample sourcetype=stream:http http_method=POST

| stats sum(bytes_out) as count by src_ip, dest_ip  
| where count >= 1377217  
| sort - count
```