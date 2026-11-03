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

 Dictionary uses several built-in methods for manipulation.  
 1. **update()** : Updates the value of the key provided to it if the item already exists in the dictionary, else it creates a new key-value pair.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
info.update({'age':20})
info.update({'DOB':2003})
print(info)
```
Output:
```
info = {"name" : "Karan", 'age':20, "eligible" : True, 'DOB':2003}
```

2. **clear()** : Removes all the items from the dictionary.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
info.clear()
print(info)
```
Output:
```
{}
```

3. **pop()** : Removes the key-value pair whose key is passed as a parameter.
```
info = {"name" : "Karan", "age" : 19, "eligible" : True}
info.pop('eligible')
print(info)
```
Output:
```
{"name" : "Karan", "age" : 19}
```

4. **popitem()** : Removes the last key-value pair from the dictionary.
```
info = {"name" : "Karan", "eligible" : True, "age" : 19}
info.popitem()
print(info)
```
Output:
```
{"name" : "Karan", "eligible" : True}
```

5. **del** : Removes a dictionary item.
```
info = {"name" : "Karan", "eligible" : True, "age" : 19}
del info['age']
print(info)
```
Output:
```
info = {"name" : "Karan", "eligible" : True}
```

If the key is not provided del keyword will delete the entire dictionary. 
