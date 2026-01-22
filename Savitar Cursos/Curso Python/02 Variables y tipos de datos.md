```python
str
cadena = "Mi cadena"

Ver tipo de dato 
print(type(cadena))

int

port= 80
print(type(port))

float 
number = 4.5
print(type(number))

Conversiones con type casting
number = float(4)
number = str(4)
number = int(4.0)

Listas
my_ports= [80,22,443]
OR
my_ports= []
my_ports.append(22)
my_ports.append(80)
my_ports.extend([86,87])
my_ports += [33,56]
print(my_ports[1])

concatenar string con int a la hora de mostrar

print (f"Puerto: {port}")

for x,y in enumerate(mi_lista):
	print(f"{x}: {y}")

indice= [x for x,y in enumerate(mi_lista) if y==12]

Tipo de datos que no admite repeticion de datos
set(mi_lista) 
```