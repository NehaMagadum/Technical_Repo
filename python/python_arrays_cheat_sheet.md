# Python Arrays
### What is Array?
An array is a collection of elements of the same data type stored under a single variable name. Arrays are useful for storing and accessing multiple values efficiently.    
**Note:** Python lists can store different data types, whereas the standard Python array module stores elements of the same type.
### Creating an Array
Python provides the array module to create arrays.
```
import array
arr = array.array('i', [10, 20, 30, 40])
print(arr)
```
• array - Module used to create arrays.  
• 'i' – Type code for signed integer.  
• [10, 20, 30, 40] – Array elements.  
### Array Type Codes.   
|Type Code | Data Type |
|----|----|
|'i' | Signed integer|
|'f' | Float|
|'d' | Double precision float|
|'b' | Signed character|
|'u' | Unicode character|
### Accessing Array Elements
Array indexing starts from 0.
```
import array
arr = array.array('i', [10, 20, 30, 40])

print(arr[0])   # 10
print(arr[1])   # 20
print(arr[-1])  # 40
```
### Updating Array Elements
```
arr[1] = 100
print(arr)
```
Output:
```
array('i', [10, 100, 30, 40])
```
### Array Methods
| Method | Definition | Example |
|----|----|-----|
|append()|Adds one element at the end|arr.append(50)|
|insert()|Inserts element at an index|arr.insert(1, 15)|
|remove()|Removes first matching element|arr.remove(20)|
|pop()|Removes and returns element|arr.pop()|
|index()|Returns index of element|arr.index(30)|
|count()|Counts occurrences|arr.count(10)|
|reverse()|Reverses array|arr.reverse()|
|tolist()|Converts array to list|arr.tolist()|
### Traversing an Array
Using for loop
```
import array
arr = array.array('i', [10, 20, 30, 40])
for num in arr:
    print(num)
```
Using Index
```
for i in range(len(arr)):
    print(arr[i])
```
### Array Operations
```
import array

arr = array.array('i', [10, 20, 30])

# Length
print(len(arr))

# Add element
arr.append(40)

# Insert element
arr.insert(1, 15)

# Remove element
arr.remove(20)

# Reverse
arr.reverse()

# Convert to list
print(arr.tolist())
```
### Array Slicing 
Slicing is used to access a portion of an array.
```
arr = array.array('i', [10, 20, 30, 40, 50])

print(arr[1:4])   # 20, 30, 40
print(arr[:3])    # 10, 20, 30
print(arr[2:])    # 30, 40, 50
print(arr[::-1])  # Reverse
```
### Array vs List
| Array | List|
|----|----|
|Same data type elements|Different data types allowed|
|Requires array module|Built-in|
|Generally memory-efficient for numeric data|More flexible|
|array.array()|[]|
