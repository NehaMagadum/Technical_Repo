# SOLID Principles in Python
SOLID is a set of 5 object-oriented design principles that help developers write clean, maintainable, reusable, and flexible code.
## 1. S - Single Responsibility Principle(SRP) 
A class should have only one responsibility or one reason to change.
```bash
class Student:
    def get_details(self):
        print("Student details")

class StudentDatabase:
    def save(self):
        print("Saving student")

class StudentReport:
    def generate(self):
        print("Generating report")
```
## 2. O - Open/Closed Principle(OCP)
Software entities should be open for extension but closed for modification.  
- Add new functionality without modifying existing working code.  
- Use inheritance or polymorphism to extend behavior.  
```bash
class Payment:
    def pay(self):
        pass

class UPI(Payment):
    def pay(self):
        print("Paying using UPI")

class Card(Payment):
    def pay(self):
        print("Paying using Card")

class Cash(Payment):
    def pay(self):
        print("Paying using Cash")
```
Usage:
```bash
payments = [UPI(), Card(), Cash()]

for payment in payments:
    payment.pay()
```
Output:
```
Paying using UPI
Paying using Card
Paying using Cash
```
## 3. L — Liskov Substitution Principle (LSP)
Objects of a child class should be usable wherever objects of the parent class are expected, without breaking the program.
```bash
class Bird:
    def eat(self):
        print("Eating")

class FlyingBird(Bird):
    def fly(self):
        print("Flying")

class Sparrow(FlyingBird):
    pass

class Penguin(Bird):
    def swim(self):
        print("Swimming")
```
Usage:
```bash
s = Sparrow()
s.fly()

p = Penguin()
p.swim()
```
Output:
```
Flying
Swimming
```
## 4. I — Interface Segregation Principle (ISP)
A class should not be forced to implement methods it does not need.
```bash
from abc import ABC, abstractmethod

class Walkable(ABC):
    @abstractmethod
    def walk(self):
        pass

class Swimmable(ABC):
    @abstractmethod
    def swim(self):
        pass

class Flyable(ABC):
    @abstractmethod
    def fly(self):
        pass
```
Implementation
```bash
class Dog(Walkable):
    def walk(self):
        print("Dog walks")

class Fish(Swimmable):
    def swim(self):
        print("Fish swims")

class Sparrow(Walkable, Flyable):
    def walk(self):
        print("Sparrow walks")

    def fly(self):
        print("Sparrow flies")
```
Now each class implements only the behavior it needs.
## 5. D — Dependency Inversion Principle (DIP)
High-level modules should not depend directly on low-level modules. Both should depend on abstractions.
```bash
from abc import ABC, abstractmethod

class Message(ABC):
    @abstractmethod
    def send(self):
        pass

class Email(Message):
    def send(self):
        print("Sending email")

class SMS(Message):
    def send(self):
        print("Sending SMS")

class Notification:
    def __init__(self, message):
        self.message = message

    def notify(self):
        self.message.send()
```
Usage:
```bash
n1 = Notification(Email())
n1.notify()

n2 = Notification(SMS())
n2.notify()
```
Output:
```
Sending email
Sending SMS
```
