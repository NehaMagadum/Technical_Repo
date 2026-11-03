# Python Dictionary

• Dictionaries are 'ordered' collection of data items.  
• They store multiple items in a single variable.  
• Dictionary items are key-value pairs that are separated by comma's and enclosed within curly brackets {}.  
Example: 
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info)
```
Output:
```
{"name" : "Karan", "age" : 19, "eligible" : True}
```

## Accessing Dictionary items

### Accessing a single value 

Values in a dictionary can be accessed using keys.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info[name])
```
Output:
```
Karan
```
Using get method 
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info.get("eligible"))
```
Output:
```
True
```
### Accessing multiple values

We can print all the values in the dictionary using values() method.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info.values())
```
Output:
```
dict_values(['Karan', 19, True])
```
### Accessing Keys

We can print all the keys in the dictionary using keys() method.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info.keys())
```
Output:
```
dict_keys(['name', 'age', 'eligible'])
```

### Accessing key-value pairs

We can print all the key-value pairs in dictionary using items() method.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
print(info.items())
```
Output:
```
dict_items([('name':'Karan'), ('age':19), ('eligible':True)])
```

 ### Dictionary Methods
