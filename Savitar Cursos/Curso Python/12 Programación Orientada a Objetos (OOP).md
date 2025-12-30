Clase en Python

```
class Persona:
	#variables de clase
	
	#constructor
	def __init__(self,nombre,edad):
		self.nombre=nombre
		self.edad=edad
	
	#Metodos
	def saludo(self):
		return f"Mi nombre es {self.nombre} y mi edad es {self.edad}"
		

marcelo=Persona("Marcelo",24)
print(marcelo.saludo())

class CuentaBancaria:
	def __init__(self, cuenta, nombre, dinero=0):
		self.cuenta=cuenta
		self.nombre=nombre
		self.dinero=dinero
	
	def depositarDinero(self,dinero):
		self.dinero+=dinero
		return f"Haz depositado {dinero} euros blance actual {self.dinero}"
```

Decoradores
```
class Rectangulo:
	#constructor
	def __init__(self,ancho,alto):
		self.ancho=ancho
		self.alto=alto
	
	#Metodos + Decoradores
	@property
	def area(self):
		return self.ancho*self.alto
	
	#Modificacion de la propiedad str	
	def __str__(self):
		return f"\n[+] Propiedades del rectangulo [Ancho:{self.ancho}][Alto: {self.alto}]"
	
	#Redefines la igualdad del objeto con respecto a otro objeto
	def __eq__(self,otro):
		retur self.alto==otro.alto and self.ancho==otro.ancho	
	
#las propiedades nos permiten acceder al metodo de la forma 
rectangulo1=Rectangulo(23,45)
rectangulo2=Rectangulo(23,46)
print(rectanfulo1)
print(f"El area del rectangulo es rectangulo1.area")		
print(f"Son iguales ---> {rectangulo1 == rectangulo2}")
```

Decoradores muy usados static method y class method

```
class Libro:
	#Variables de clase
	IVA=0.21
	def __init__(self,titulo,autor,precio):
		self.titulo=titulo
		self.autor=autor
		self.precio=precio
	
	#Decorador staticmethod
	@staticmethod
	def es_bestseller(total_ventas):
		return total_ventas > 5000
	#Decorador classmethod
	@classmethod
	def precio_iva(cls,precio):
		return precio+precio*cls.IVA

#Herencia
class LibroDigital(Libro):
	IVA=1.40


mi_libro=Libro("Amanecer","Frank",25)
mi_libro_digital=LibroDigital("Anochecer","Frank",25)
Para acceder a los metodos staticos no es necesario referenciar al obj 
print(Libro.es_bestseller(7000))
print(LibroDigital.precio_iva(mi_libro_digital.precio))

```