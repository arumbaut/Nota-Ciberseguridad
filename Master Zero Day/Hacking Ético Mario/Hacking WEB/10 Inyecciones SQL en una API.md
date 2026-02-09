- Tags : #apis #sql #sqlinjection #recursos_dockerlabs 

**Recurso** maquina APIbase *docklerlans.es*

Encontrar parametros de un endpoint de una api con dirb

```bash
dirb http://url:port/endpoint?

Intentar la inyeccion sql del parametro encontrado
dirb http://url:port/endpoint?username=' or 1=1-- - 

```