Herencia
```
class Animal:
	def __init__(self,nombre):
		self.nombre=nombre
	#Metodo astracto
	def hablar(self):
		rise NotImplementedError("Las subclases deben impementar este metodo") 
		#Podemos poner rise o pass
		pass
#Herencia
class Perro(Animal):
	def hablar(self):
		return f"{self.nombre} dice jau jau"

class Gato(Animal):
	def hablar(self):
		return f"{self.nombre} dice miau miau"
		
		
perro=Perro("King")
print(f"{perro.hablar}")
```

Utilizar el constructor del padre y del hijo con super esto sirve tanto para el constructor  como para los métodos de la clase
```
#!/usr/bin/env python3

class A:
    def __init__(self, x):
        self.x = x
        print(f"Valor en x: {self.x}")

class B(A):
    def __init__(self, x, y):
        print("Inicializando B")
        super().__init__(x)
        self.y = y
        print(f"Valor en Y: {self.y} y Valor en X: {self.x}")

# Basado en los comentarios de la imagen, 
# la ejecución sería:
b = B(2, 10)

# Salida esperada:
# Inicializando B
# Valor en x: 2
# Valor en y: 10
```



Polimorfismo
```
class Vehicle:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
  def move(self):  
    print("Move!")  
  
class Car(Vehicle):  
  pass  
  
class Boat(Vehicle):  
  def move(self):  
    print("Sail!")  
  
class Plane(Vehicle):  
  def move(self):  
    print("Fly!")  
  
car1 = Car("Ford", "Mustang")       #Create a Car object  
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat object  
plane1 = Plane("Boeing", "747")     #Create a Plane object  
  
for x in (car1, boat1, plane1):  
  print(x.brand)  
  print(x.model)  
  x.move()
```

**Herencia**

Es un principio de la POO que permite a una clase heredar atributos y métodos de otra clase, conocida como su clase base o superclase. La herencia facilita la reutilización de código y la creación de una jerarquía de clases. Las subclases heredan las características de la superclase, lo que permite que se especialicen o modifiquen comportamientos existentes.

**Polimorfismo**

Este concepto se refiere a la habilidad de objetos de diferentes clases de ser tratados como instancias de una clase común. El polimorfismo permite que una función o método interactúe con objetos de diferentes clases y los trate como si fueran del mismo tipo, siempre y cuando compartan la misma interfaz o método. Esto significa que el mismo método puede comportarse de manera diferente en distintas clases, un concepto conocido como sobrecarga de métodos.