# Python OOP
## What is OOP?
OOP stands for Object-Oriented Programming.  
Python is an object-oriented language, allowing you to structure your code using classes and objects for better organization and reusability. 

## Advantages of OOP
- Provides a clear structure to program.  
- Makes code easier to maintian, reuse, and debug.  
- Helps keep your code DRY (Don't Repeat Yourself).

## What are Classes and Objects?
**Class** - A class is a blueprint or a template for creating an object.  
**Object** - Object is the instance of the class used to access the properties of the class.
### Creat a Class
```bash
class MyClass:
    x = 5
```
### Create Object
```bash
p1 = MyClass()
print(p1.x)
```
### Delete Objects
You can delete objects by using the 'del' keyword.  
Example:
```bash
del p1
```
### Multiple Objects 
You can create multiple objets from the same class.  
Example:
```bash
p1 = MyClass()
p2 = MyClass()
p3 = MyClass()

print(p1.x)
print(p2.x)
print(p3.x)
```
## The pass Statement
class definitions cannot be empty, but if you for some reason have a class definition with no content, put in the passvstatement to avoid getting an error.  
Example:
```bash
class Person:
    pass
```
## The __init__() method
All classes have a built-in method called __init__(), which is always executed when the class is being initiated.
```bash
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("Emil", 36)

print(p1.name)
print(p1.age)
```
Output:
```
Emil
36
```
## The self Parameter
The self parameter is reference to the current instance of the class.It is used to access properties and methods that belong to the class.
```bash
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def greet(self):
    print("Hello, my name is " + self.name)

p1 = Person("Emil", 25)
p1.greet()
```
Output:
```
Hello, my name is Emil
```
- Without self, Python would not know which object's properties you want to access.  
- IT does not have to be named self, you can call it whatever you like, but it has to be the first parameter of any method in the class.

### Accessing properties with self
You can access any property of the class using self.  
Example:
```bash
class Car:
  def __init__(self, brand, model, year):
    self.brand = brand
    self.model = model
    self.year = year

  def display_info(self):
    print(f"{self.year} {self.brand} {self.model}")

car1 = Car("Toyota", "Corolla", 2020)
car1.display_info()
```
Output:
```
2020 Toyota Corolla
```
### Calling methods with self
You can also call other methods using self
```bash
class Person:
  def __init__(self, name):
    self.name = name

  def greet(self):
    return "Hello, " + self.name

  def welcome(self):
    message = self.greet()
    print(message + "! Welcome to our website.")

p1 = Person("Tobias")
p1.welcome()
```
Output:
```
Hello Tobias! Welcome to our website.
```
## Constructors
- Special method in a class used to create and initialize an object of a class.  
- Constructor is invoked automatically when an object of a class is created.  
**Syntax** :
```bash
def __init__(self):
```
We can also create constructor by defining the function name with same class name.  
```bash
class Abc:
    def Abc(self):
```
**Types**
1. **Default Constructor** - Constructor which doesn't accept any arguments from object and has only one argument self.  
Example:
```bash
class Details:
    def __init__(self):
        print("Hi")
d1 = Details()
```
Output:
```
Hi
```

2. **Parameterized Constructor** - Constructor which accepts arguments along with self. 
## Python Class Properties
Properties are variables that belong to class. They store data for each object created from the class.  
Example:
```bash
class Details:
    def __init__(self,name):
        self.name = name
d1 = Details("Kiefer")
print(d1.name)
```
Output:
```
Kiefer
```

### Access Properties
You can access object properties using don(.) notation.  
Example:
```bash
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("Emil", 36)

print(p1.name)
print(p1.age)
```
### Modified Properties
You can modify the value of properties on objects.  
Example:
```bash
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("Tobias", 25)
print(p1.age)

p1.age = 26
print(p1.age)
```
Output:
```
25
26
```
### Delete Properties
You can delete properties from objects using the 'del' keyword.  
Example:
```bash
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("Linus", 30)

del p1.age

print(p1.name) # This works
# print(p1.age) # This would cause an error
```
### Class Proerties vs Object Properties
**Instance properties** - Properties defined inside __init__() belong to each object.  
**Class properties** - Properties defined outside methods belong to the class itself and are shared by all objects.  
Example:
```bash
class Person:
  species = "Human" # Class property

  def __init__(self, name):
    self.name = name # Instance property

p1 = Person("Emil")
p2 = Person("Tobias")

print(p1.name)
print(p2.name)
print(p1.species)
print(p2.species)
```
Output:
```
Emil
Tobias
Human
Human
```
### Modifying Class properties 
When you modify a class property, it affects all objects.  
Example:
```bash
class Person:
  lastname = ""

  def __init__(self, name):
    self.name = name

p1 = Person("Linus")
p2 = Person("Emil")

Person.lastname = "Refsnes"

print(p1.lastname)
print(p2.lastname)
```
Output:
```
Refsnes
```
### Add new properties
You can add new properties to existing objects.  
Example:
```bash
class Person:
  def __init__(self, name):
    self.name = name

p1 = Person("Tobias")

p1.age = 25
p1.city = "Oslo"

print(p1.name)
print(p1.age)
print(p1.city)
```
Output:
```
Tobias
25
Oslo
```
## Decorators
Powerful and versatile tool that allow to modify the behavior of function or method.  
**Syntax**:  
```bash
@decorator_function
def my_fun():
    pass
```
### Getters and Setters
**Getters** : Used to access the value of an objects properties and to return the value of a sepecific property.
```bash
class Myclass:
    def __init__(self,value):
        self._value = value

    @property
    def value(self):
        return self._value

obj = Myclass(10)
obj.value
```
Output:
```
10
```
**Setters** : Getters do not take any parameters and e can not set the value through getter method for that we need setters method which can be added by decorating method '@property_name.setter'.  
```bash
class Myclass:
    def __init__(self,value):
        self._value = value

    @property
    def value(self):
        return self._value

    @value.setter
    def value(self,new_value):
        self._value = new_value
obj = Myclass(10)
obj.value = 20
obj.value
```
Output:
```
20
```
### Static Method
- Methods that belong to a class rather than an instance of the class.  
- They are defined using the '@staticmethod' decorator and do not have access to the instance of the class.
```bash
class Math:
    @staticmethod
    def add(a,b):
        return a+b
result = Math(1,2)
print(result)
```
Output:
```
3
```
### Class Method
A class method is a type of method that is bound to the class and not to the instance of the class.
```bash
class ExampleClass:
    @classmethod
    def factory_method(cls,argument1,argument2):
        return cls(argument1,argument2)
```
## Inheritance
Inheritance allows us to define a class that inherits all the methods and properties from another class.  

**Parent class** is the class being inherited from, also called base class.  

**Child class** is the class that inherits from another class, also called derived class.  
**Example:** Create a class named Person, with firstname and lastname properties, and a printname method, Create a class named Student, which will inherit the properties and methods from the Person class, Use the Student class to create an object, and then execute the printname method.
```bash
class Person:
  def __init__(self, fname, lname):
    self.firstname = fname
    self.lastname = lname

  def printname(self):
    print(self.firstname, self.lastname)

class Student(Person):
  pass

x = Person("John", "Doe")
x.printname()

x = Student("Mike", "Olsen")
x.printname()
```
Output:
```
John, Doe
Mike, Olsen
```
### Use the super() Function
Python also has a 'super()' function that will make the child class inherit all the methods and properties from its parent.
```bash
class Parent:
    def __init__(self):
        print("Parent constructor")
    def show(self):
        print("Parent method")
class Child(Parent):
    def __init__(self):
        super().__init__()
        print("Child constructor")
    def display(self):
        super().show()
        print("Child method")
c = Child()
c.display()
```
Output:
```
Parent constructor
Child constructor
Parent method
Child method
```
**Types Of Inheritance**
1. **Single Inheritance** : One child class inherits from one parent class.
```bash
class Animal:
    def eat(self):
        print("Animal is eating")

class Dog(Animal):
    def bark(self):
        print("Dog is barking")

d = Dog()
d.eat()
d.bark()
```
Output:
```
Animal is eating
Dog is barking
```
2. **Multiple Inheritance** : One child class inherits from two or more parent classes.
```bash
class Father:
    def father_skill(self):
        print("Gardening")

class Mother:
    def mother_skill(self):
        print("Cooking")

class Child(Father, Mother):
    def own_skill(self):
        print("Programming")

c = Child()
c.father_skill()
c.mother_skill()
c.own_skill()
```
Output:
```
Gardening
Cooking
Programming
```
3. **Multilevel Inheritance** : A class inherits from a child class, forming a chain of inheritance.
```bash
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

class Puppy(Dog):
    def weep(self):
        print("Weeping")

p = Puppy()
p.eat()
p.bark()
p.weep()
```
Output:
```
Eating
Barking
Weeping
```
4. **Hierarchical Inheritance** :  Multiple child classes inherit from the same parent class.
```bash
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

class Cat(Animal):
    def meow(self):
        print("Meowing")

class Cow(Animal):
    def moo(self):
        print("Mooing")

d = Dog()
c = Cat()
w = Cow()
d.eat()
c.eat()
w.eat()
```
Output:
``` 
Eating
Eating
Eating
```
5. **Hybrid Inheritance** : Hybrid inheritance is a combination of two or more types of inheritance.
```bash
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

class Cat(Animal):
    def meow(self):
        print("Meowing")

class Puppy(Dog, Cat):
    def play(self):
        print("Playing")

p = Puppy()
p.eat()
p.bark()
p.meow()
p.play()
```
Output:
```
Eating
Barking
Meowing
Playing
```
## Polymorphism
Polymorphism means one interface, multiple forms. The same method or operation can behave differently for different objects.  
**Method Overloading** : Child class provides its own implementation of a parent method.
```bash
class Animal:
    def sound(self):
        print("Animal sound")

class Dog(Animal):
    def sound(self):
        print("Bark")

class Cat(Animal):
    def sound(self):
        print("Meow")

Dog().sound()
Cat().sound()
```
Output:
```
Bark
Meow
```
**Duck Typing** : Duck typing is a concept in Python where an object's suitability is determined by the methods and attributes it supports rather than its actual class or type.  
Example:
```bash
class Dog:
    def sound(self):
        print("Dog barks")

class Cat:
    def sound(self):
        print("Cat meows")

def make_sound(animal):
    animal.sound()

d = Dog()
c = Cat()
make_sound(d)
make_sound(c)
```
Output:
```
Dog barks
Cat meows
```
**Operator Overloading** : Operator overloading allows operators such as +, -, *, == etc. to behave differently for user-defined objects.Python implements operator overloading using special methods (magic methods).
```bash
class Number:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return self.value + other.value

n1 = Number(10)
n2 = Number(20)
print(n1 + n2)
```
Output:
```
30
```
**Method Overloading** : 
- Method overloading means defining multiple methods with the same name but different numbers or types of parameters.  
- Languages like Java support traditional method overloading.  
- Python does not support traditional method overloading directly.  
- If multiple methods with the same name are defined in a class, the latest definition replaces the previous one.  
- We can achieve similar behavior using default arguments, *args, or conditional logic.  
```bash
class Calculator:
    def add(self, a, b=0, c=0):
        return a + b + c

obj = Calculator()
print(obj.add(10, 20))
print(obj.add(10, 20, 30))
print(obj.add(10))
```
Output:
```
30
60
10
```
## Abstraction
Abstraction means hiding implementation details and showing only essential functionality.
```bash
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        print("Bark")

obj = Dog()
obj.sound()
```
Output:
```
Bark
```
## Encapsulation
Encapsulation means combining data and methods inside a class and controlling access to the data.  
**Access Modifiers in Python**
|Modifier|Syntax|Meaning|
|----|----|----|
|Public|name|Accessible everywhere|
|Protected|_name|Intended for internal/subclass use|
|Private|__name|Name-mangled to discourage direct access|

```bash
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.__marks = marks

    def get_marks(self):
        return self.__marks

    def set_marks(self, marks):
        if marks >= 0:
            self.__marks = marks

s = Student("Neha", 90)
print(s.name)
print(s.get_marks())
s.set_marks(95)
print(s.get_marks())
```
Output:
```
Neha
90
95
```

## Magic Methods (Dunder Methods)
- Magic methods are special methods in Python that have double underscores before and after their names.  
- They are also called Dunder (Double Underscore) methods.  
- They allow us to define how objects behave with built-in operations such as printing, comparison, arithmetic, iteration, and object creation.  
- Python automatically calls these methods when the corresponding operation is performed.  
**Common Magic Methods**  

| Magic Method | Purpose |
|---|---|
| `__init__()` | Initializes an object's attributes. |
| `__new__()` | Creates and returns a new object. |
| `__str__()` | Defines the user-friendly string representation of an object. |
| `__repr__()` | Defines the developer-oriented representation of an object. |
| `__len__()` | Defines the behavior of `len()`. |
| `__add__()` | Defines the behavior of `+`. |
| `__sub__()` | Defines the behavior of `-`. |
| `__mul__()` | Defines the behavior of `*`. |
| `__eq__()` | Defines the behavior of `==`. |
| `__lt__()` | Defines the behavior of `<`. |
| `__gt__()` | Defines the behavior of `>`. |
| `__contains__()` | Defines the behavior of `in`. |
| `__getitem__()` | Defines indexing using `[]`. |
| `__setitem__()` | Defines assignment using `[]`. |
| `__delitem__()` | Defines deletion using `del obj[key]`. |
| `__iter__()` | Returns an iterator. |
| `__next__()` | Returns the next item from an iterator. |
| `__call__()` | Allows an object to be called like a function. |
| `__del__()` | Called during object finalization. |
