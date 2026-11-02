# Python
Python is a high level, interpreted programming language known for it's simplicity, readability, and versatility.  
## Key features of Python
• Easy to learn.   
• Versatile.  
• Extensive libraries.  
• Cross - platform.   
• Dynamic typing.  
## Getting Started
Start the interactive shell.
```
$ python
```
Quit the interactive shell.
```
>>> exit()
```
Run a Script.
```
$ python my_script.py
```
Run a script in interactive mode.
```
$ python -i my_script.py
```
## Comments
A comment is a part of the coding file that the programmer doesn't want to execute, rather the programmer uses it to either explain a block of code or to avoid the execution of a specific part of code while testing.
```
# This is a comment.
```
## Variables 
It is a container that holds data.  
Example:  
```
a = 1
b = True
```
## Data Types
It specifies the type of value a variable holds.      
1. **Numeric data :** int, float, complex.  
Examples:
```
a = 12    # int
b = 13.6  # float
c = 2+8i  # complex
```
2. **Text data :** String.  
Example:
```
name = "Neha"
```
3. **Boolean data :** True, False
4. **Sequence data :** List, Tuple
5. **Mapped data :** Dictionary
## Operators 
Python has different types of operators for different operations.    
1. **Arithmetic Operators :** +, -, *, / , //, %, **.   
2. **Assignment and Augmented Operators :** =, +=, -=, *=, /=, %=, //=, **==.   
3. **Comparison Operators :** ==, !=, >, <, >=, <=.   
4. **Logical Operators :** and, or, not.   
5. **Identity Operators :** is, is not.   
6. **Membership Operators :** in, not in.   
7. **Bitwise Operators :** &, |, ^, ~, <<, >>.   
## Type Casting or Type Conversion
The conversion of one data type into the other data type is known as type casting or type conversion.    
Two types :
1. **Explicit Conversion :** The conversion of one data type to other is done by developers.
2. **Implicit Conversion :** The conversion of one data type to other is automatically done by python.  
## Conditional Statements
A conditional statement executes a block of code based on whether a condition is true or false.  
Examples: if, elif, else.
### if 
```
if age >= 18:
    print("Adult")
```
### elif
```
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
```
### else
```
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")
```
## Loops
A loop is used to execute a block of code repeatedly until a condition is satisfied or a sequence is completed.  
Types:  
• for loop.   
• while loop. 
### For Loop
```
for i in range(5):
    print(i)
```
### Range
```
range(5)        # 0 to 4
range(1, 6)     # 1 to 5
range(1, 10, 2) # 1, 3, 5, 7, 9
```
### While Loop
```
i = 1
while i <= 5:
    print(i)
    i += 1
```
### Loop Control
```
break       # Exit loop
continue    # Skip current iteration
pass        # Empty statement
```

