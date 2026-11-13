# Strings
- In Python anything that you enclose between a string.
- A String is essentially a sequence or array of textual data.
- Strings are used when working with unicode characters.
**Example** -
```bash
name = "Harry"
print("Hello",name)
```
Output:
```
Hello Harray
```

## Accessing characters of a string
We can access parts of string by using it's index which starts from 0.  
Example:
```bash
name = "Harry"
print(name[0])
print(name[1])
```
Output:
```
H
a
```

## Looping through the string
We can loop throughstrings using a for loop like this:
```bash
name = "Harry"
for character in name:
    print(character)
```
output:
```
H
a
r
r
y
```
## String slicing and operations on string
**Length of a string** - We can find the length of astring using len() function.
```bash
fruit = "Mango"
len1 = len(fruit)
print("Mango is a ",len1,"letter word.")
```
Output:
```bash
Mango is a 5 letter word.
```

## String as an array
A String is essentially a sequance of characters also called an array. Thus we can access the elements of this array.
```bash
pic = "Applepic"
print(pic[:5])
print(pic[6])
```
Output:
```
Apple
i
```

## Loop through a string
Strings are arrays and arrays are iterable. Thus we can loop through strings.
```bash
alphabets = "ABCDE"
for i in alphabets:
    print(i)
```
Output:
```
A
B
C
D
E
```

## String Methods
We can use string methods to alter and modify the string.

### 1. upper()
Converts a strings to uppercase.
```bash
str1 = "abcdef"
print(str1.uppercase())
```
**Output:**
```
ABCDEF
```

## 2. lower()

- Converts all characters in a string into lowercase.

```python
text = "HELLO WORLD"
print(text.lower())
```

**Output:**
```text
hello world
```

## 3. strip()

- Removes spaces from both the beginning and end of a string.
- Does not remove spaces between words.

```python
text = "   Hello World   "
print(text.strip())
```

**Output:**
```text
Hello World
```

## 4. rstrip()

- Removes spaces from the right side (end) of a string.

```python
text = "Hello World   "
print(text.rstrip())
```

**Output:**
```text
Hello World
```

## 5. replace()

- Replaces a specific character or word with another character or word.

**Syntax:**
```python
string.replace(old, new)
```

```python
text = "Hello World"
print(text.replace("World", "Python"))
```

**Output:**
```text
Hello Python
```

## 6. split()

- Splits a string into a list based on a separator.
- By default, it splits using whitespace.

```python
text = "Python Java C++"
print(text.split())
```

**Output:**
```python
['Python', 'Java', 'C++']
```

Another example:

```python
text = "apple,banana,mango"
print(text.split(","))
```

**Output:**
```python
['apple', 'banana', 'mango']
```

## 7. capitalize()

- Converts the first character of a string into uppercase.
- Converts all remaining characters into lowercase.

```python
text = "hello WORLD"
print(text.capitalize())
```

**Output:**
```text
Hello world
```

## 8. center()

- Places a string in the center of a specified width.
- Adds spaces on both sides by default.

**Syntax:**
```python
string.center(width)
```

```python
text = "Python"
print(text.center(12))
```

**Output:**
```text
   Python   
```

We can also specify a filling character:

```python
text = "Python"
print(text.center(12, "*"))
```

**Output:**
```text
***Python***
```

## 9. count()

- Counts how many times a particular character or substring occurs in a string.

```python
text = "banana"
print(text.count("a"))
```

**Output:**
```text
3
```

## 10. endswith()

- Checks whether a string ends with a specified character or word.
- Returns `True` or `False`.

```python
text = "hello.py"
print(text.endswith(".py"))
```

**Output:**
```text
True
```

## 11. find()

- Returns the index (position) of the first occurrence of a specified character or substring.
- Returns `-1` if the substring is not found.

```python
text = "Hello World"
print(text.find("World"))
print(text.find("Python"))
```

**Output:**
```text
6
-1
```

## 12. index()

- Returns the index (position) of the first occurrence of a specified character or substring.
- Raises a `ValueError` if the substring is not found.

```python
text = "Hello World"
print(text.index("World"))
```

**Output:**
```text
6
```

**Difference between find() and index():**

| find() | index() |
|---|---|
| Returns -1 if not found. | Raises ValueError if not found. |
| Does not produce an error for missing values. | Produces an error for missing values. |

## 13. isalnum()

- Checks whether all characters in a string are alphabets or numbers.
- Does not allow spaces or special characters.
- Returns `True` or `False`.

```python
text = "Python123"
print(text.isalnum())
```

**Output:**
```text
True
```

## 14. isalpha()

- Checks whether all characters in a string are alphabets.
- Does not allow numbers, spaces, or special characters.

```python
text = "Python"
print(text.isalpha())
```

**Output:**
```text
True
```

## 15. islower()

- Checks whether all cased characters in a string are lowercase.
- Returns `True` or `False`.

```python
text = "hello"
print(text.islower())
```

**Output:**
```text
True
```

## 16. isprintable()

- Checks whether all characters in a string are printable.
- Newline (`\n`) and tab (`\t`) are not printable.

```python
text = "Hello World"
print(text.isprintable())
```

**Output:**
```text
True
```

Another example:

```python
text = "Hello\nWorld"
print(text.isprintable())
```

**Output:**
```text
False
```

## 17. isspace()

- Checks whether all characters in a string are whitespace characters (spaces, tabs, newlines).
- Returns `True` or `False`.

```python
text = "   "
print(text.isspace())
```

**Output:**
```text
True
```

## 18. istitle()

- Checks whether each word starts with an uppercase letter and the remaining cased letters are lowercase.

```python
text = "Hello World"
print(text.istitle())
```

**Output:**
```text
True
```

Another example:

```python
text = "hello world"
print(text.istitle())
```

**Output:**
```text
False
```

## 19. startswith()

- Checks whether a string starts with a specified character or word.
- Returns `True` or `False`.

```python
text = "Python Programming"
print(text.startswith("Python"))
```

**Output:**
```text
True
```

## 20. swapcase()

- Converts uppercase characters into lowercase and lowercase characters into uppercase.

```python
text = "Hello WORLD"
print(text.swapcase())
```

**Output:**
```text
hELLO world
```

## 21. title()

- Converts the first character of every word into uppercase and the remaining cased characters into lowercase.

```python
text = "python programming language"
print(text.title())
```

**Output:**
```text
Python Programming Language
```

---

## Quick Revision Table

| Method | Purpose |
|---|---|
| `lower()` | Converts string to lowercase |
| `strip()` | Removes spaces from both ends |
| `rstrip()` | Removes spaces from the right side |
| `replace()` | Replaces a word or character |
| `split()` | Splits string into a list |
| `capitalize()` | Capitalizes the first character |
| `center()` | Aligns string in the center |
| `count()` | Counts occurrences |
| `endswith()` | Checks the ending of a string |
| `find()` | Finds index; returns -1 if not found |
| `index()` | Finds index; raises error if not found |
| `isalnum()` | Checks alphabets and numbers |
| `isalpha()` | Checks alphabets only |
| `islower()` | Checks lowercase |
| `isprintable()` | Checks printable characters |
| `isspace()` | Checks whitespace characters |
| `istitle()` | Checks title case |
| `startswith()` | Checks the beginning of a string |
| `swapcase()` | Swaps uppercase and lowercase |
| `title()` | Capitalizes every word |

## Important Points to Remember

1. String methods do not modify the original string because strings are immutable in Python.
2. Most string methods return a new string.
3. `find()` and `index()` are used to search for a substring.
4. `strip()`, `lstrip()`, and `rstrip()` are used to remove characters from string boundaries.
5. Methods starting with `is` return Boolean values (`True` or `False`).
