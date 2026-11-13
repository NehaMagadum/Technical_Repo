# Aggregations, Filters in queries
## A. Aggregate Functions
Aggregate functions perform calculations on multiple rows and return a single result. 

**Important aggregate functions**
|Function	|Meaning|
|-----|----|
|COUNT()|	Counts rows or non-NULL values|
|SUM()|	Calculates total|
|AVG()|	Calculates average|
|MIN()|	Returns minimum value|
|MAX()|	Returns maximum value|

### Examples:  
Table name: Employees
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|1|Rahul|10|50000|
|2|Priya|20|60000|
|3|Amit|10|45000|
|4|Neha|NULL|40000|
### COUNT()
```bash
SELECT COUNT(*) FROM Employees;
```
Output:
```
4
```
It counts all rows
```bash
SELECT COUNT(dept_id) FROM Employees;
```
Output: 
```
3
```
It counts non-NULL department IDs.

### SUM()
```bash
SELECT SUM(salary) FROM Employees;
```
Output:
```
195000
```

### AVG()
```bash
SELECT AVG(salary) FROM Employees;
```
Output:
```
48750
```

### MIN()
```bash
SELECT MIN(salary)
FROM Employees;
```
Output:
```
40000
```

### MAX()
```bash
SELECT MAX(salary)
FROM Employees;
```
Output:
```
60000
```

## B. GROUP BY
GROUP BY is used to group rows having the same values and apply aggregate functions to each group.  

Example: Calculate department-wise average salary.
```bash
SELECT dept_id, AVG(salary)
FROM Employees
GROUP BY dept_id;
```
Output:
|dept_id|	AVG(salary)|
|-----|-----|
|10	|47500|
|20|	60000|
|NULL|	40000|

## C. HAVING
HAVING is used to filter grouped results.  

Example: Find departments having average salary greater than ₹45,000.
```bash
SELECT dept_id, AVG(salary)
FROM Employees
GROUP BY dept_id
HAVING AVG(salary) > 45000;
```
Output:
|dept_id|	AVG(salary)|
|----|----|
|10|	47500|
|20	|60000|

## D. WHERE vs HAVING
|WHERE|	HAVING|
|-----|-------|
|Filters individual rows	|Filters groups|
|Applied before GROUP BY|	Applied after GROUP BY|
|Aggregate conditions generally cannot be used directly|	Aggregate conditions can be used|


Example using both:
```bash
SELECT dept_id, AVG(salary)
FROM Employees
WHERE salary > 40000
GROUP BY dept_id
HAVING AVG(salary) > 45000;
```
Output:
|dept_id|AVG(salary)|
|------|-----|
|10|47500|
|20|60000|

## E. Other query filters
### 1. WHERE
```bash
SELECT * FROM Employees
WHERE salary > 50000;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|2|Priya|20|60000|

### 2. AND
```bash
SELECT * FROM Employees
WHERE salary > 40000
AND dept_id = 10;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|1|Rahul|10|50000|
|3|Amit|10|45000|

### 3. OR
```bash
SELECT * FROM Employees
WHERE dept_id = 10
OR dept_id = 20;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|1|Rahul|10|50000|
|2|Priya|20|60000|
|3|Amit|10|45000|

At least one condition must be true.

### 4. BETWEEN
```bash
SELECT * FROM Employees
WHERE salary BETWEEN 40000 AND 60000;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|1|Rahul|10|50000|
|2|Priya|20|60000|
|3|Amit|10|45000|
|4|Neha|NULL|40000|

Includes both boundary values.

### 5. IN
```bash
SELECT * FROM Employees
WHERE dept_id IN (10, 20);
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|1|Rahul|10|50000|
|2|Priya|20|60000|
|3|Amit|10|45000|

Matches any value in the given list.

### 6. LIKE
```bash
SELECT * FROM Employees
WHERE name LIKE 'A%';
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|3|Amit|10|45000|


|Pattern|	Meaning|
|-------|------|
|'A%'|	Starts with A|
|'%a'|	Ends with a|
|'%ha%'|	Contains ha|
|'_a%'|	Second character is a|

- % represents zero or more characters.
- _ represents exactly one character.

### 7. IS NULL
```bash
SELECT * FROM Employees
WHERE dept_id IS NULL;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|4|Neha|NULL|40000|

## F. ORDER BY
Used to sort query results.
```bash
SELECT * FROM Employees
ORDER BY salary DESC;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|2|Priya|20|60000|
|1|Rahul|10|50000|
|3|Amit|10|45000|
|4|Neha|NULL|40000|

- ASC – Ascending order
- DESC – Descending order

## G. LIMIT
Used to restrict the number of returned rows.
```bash
SELECT * FROM Employees
ORDER BY salary DESC
LIMIT 2;
```
Output:
|emp_id|name|dept_id|salary|
|------|------|-------|------|
|2|Priya|20|60000|
|1|Rahul|10|50000|

Returns the two highest-paid employees.
