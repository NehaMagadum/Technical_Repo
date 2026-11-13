# Normalization
Normalization is the process of organizing data into multiple related tables to:
- Reduce data duplication.
- Avoid data inconsistencies.
- Improve data integrity.
- Avoid database anomalies.

## Why Normalization is required?
Consider this table:
|student_id|	student_name|	course_id|course_name|
|------|--------|---------|-------|
|1	|Rahul|	C1|	Java|
|2|	Priya|	C1	|Java|
|3|	Amit|	C2|	Python|

- Here, the course name is repeated.  
- If the course name changes, multiple rows must be updated.  
- This can cuase an update anomaly.  

### Types Of Anomalies.
1. **Insertion anomaly** : Cannot insert certain information without inserting unrelated information.  
2. **Update anomaly** : Same information must be updated in multiple rows.  
3. **Deletion anomaly** : Deleting one record unintentionally removes other useful information.

### Types Of Normalization
### 1NF - First Normal Form
A table is in 1NF when:
- Every column contains atomic values.
- No multiple values are stored in one cell.
- No repeating groups exist.

Example;
|student_id|	phone_number|
|----|----|
|1|	9876|
|1|	8765|

Each cell contains a single value.

### 2NF - Second Normal Form
A table is in 2NF when:
- It is already in 1NF.
- Every non-key attribute depends on the whole candidate key, not just part of it.

This mainly matters the primary key is composite.  

Example:
|student_id|	course_id|	student_name|	course_name|
|-----|-|---|---|
|1|	C1|	Rahul|	Java|
|1	|C2|	Rahul|	Python|

Composite key: (student_id,course_id)
- student_id → student_name
- course_id → course_name

But student_name depends only on student_id, and course_name depends only on course_id.  
These are partial dependencies.  
To achieve 2NF, divide the table into:  
**Students**
|student_id|	student_name|
|----|----|
|1|	Rahul|

**Courses**
|course_id	|course_name|
|----|----|
|C1	|Java|
|C2|	Python|

**Enrollments**
|student_id	|course_id|
|---|----|
|1	|C1|
|1	|C2|

Now non-key attributes depend on the whole key in their respective tables.

### 3NF - Third Normal Form
A table is in 3NF when:
- It is already in 2NF.
- No non-key attribute depends transitively on another non-key attribute.  

Example:
|emp_id|emp_name|	dept_id|	dept_name|
|----|-----|-----|----|
|1|	Rahul	|10|	IT|
|2|	Priya|	20|	HR|

Dependencies:
- emp_id → dept_id
- dept_id → dept_name

Therefore:

emp_id → dept_id → dept_name  

Here, department name depends indirectly on employee ID through department ID.  

To achieve 3NF:  

**Employees**
|emp_id|	emp_name|	dept_id|
|----|----|----|
|1	|Rahul|	10|
|2|	Priya	|20|

**Departments**
|dept_id|	dept_name|
|-----|------|
|10	|IT|
|20	|HR|

### BCNF - Boyce-Codd Normal Form
BCNF is a stronger version of 3NF.  

A table is in BCNF when:  

**Every determinant must be a candidate key.**  
A determinant is an attribute or set of attributes that determines another attribute.  

BCNF handles certain dependency cases that 3NF may allow.  

**Normalization summary**  
|Normal Form|	Main Requirement|
|----|------|
|1NF|	Atomic values|
|2NF|	No partial dependency|
|3NF|	No transitive dependency|
|BCNF|	Every determinant is a candidate key|

**Note**: Normalization reduces redundancy, while denormalization may improve read performance in some applications.
