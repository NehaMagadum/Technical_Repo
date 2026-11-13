# Triggers
A trigger is a database object that automatically executes when a specified event occurs on a table.  
Triggers are commanly used for:
- Auditing changes.
- maintaining logs.
- Enforcing business rules.
- Automatically updating related information.
- Tracking INSERT, UPDATE, and DELETE operations.

## Types of Triggers
Triggers are classified based on timing and event.
## A. Based on Timing
### 1. BEFORE Trigger
- Executes before the database operation.
- Example: Validate employee salary before insertion.

### 2. AFTER Trigger
- Executes after the database operation successfully occurs.
- Example: Record inserted employee details into an audit table.

## B. Based on event
|Trigger|	Executes when|
|-----|-----|
|INSERT|	New row is inserted|
|UPDATE|	Existing row is updated|
|DELETE|	Row is deleted|

Common combinations:
- BEFORE INSERT
- AFTER INSERT
- BEFORE UPDATE
- AFTER UPDATE
- BEFORE DELETE
- AFTER DELETE

### Example: AFTER INSERT Trigger in MySQL
Suppose we have two tables.  

**Employees**
```bash
CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    salary INT
);
```
**Employee_Audit**
```bash
CREATE TABLE Employee_Audit (
    audit_id INT AUTO_INCREMENT PRIMARY KEY,
    emp_id INT,
    action VARCHAR(20),
    audit_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
Now create a trigger:
```bash
DELIMITER //

CREATE TRIGGER after_employee_insert
AFTER INSERT ON Employees
FOR EACH ROW
BEGIN
    INSERT INTO Employee_Audit(emp_id, action)
    VALUES (NEW.emp_id, 'INSERT');
END//

DELIMITER ;
```
Insert an employee:
```bash
INSERT INTO Employees
VALUES (1, 'Rahul', 50000);
```
Automatically, the trigger inserts a corresponding audit record into Employee_Audit.

### NEW and OLD Keywords
In MySQL triggers:
|Keyword	|Meaning|
|----|----|
|NEW	|New row values|
|OLD|	Previous row values|

Examples:
- INSERT → NEW available.
- UPDATE → NEW and OLD available.
- DELETE → OLD available.

### Example: AFTER UPDATE Trigger
```bash
DELIMITER //

CREATE TRIGGER after_salary_update
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
    INSERT INTO Employee_Audit(emp_id, action)
    VALUES (NEW.emp_id, 'UPDATE');
END//

DELIMITER ;
```
Whenever an employee's record is updated, an audit entry is created.

### Advantages of Triggers
- Automatic execution.
- Helps maintain audit records.
- Useful for enforcing certain database rules.
- Reduces repeated application-side logic.

### Disadvantages of Triggers
- Difficult to debug.
- Can make database behavior less visible.
- May affect performance.
- Complex triggers can cause unexpected side effects.


|Stored Procedure|	Trigger|
|------|------|
|Called explicitly|	Executes automatically|
|Can accept parameters|	Trigger parameters are not passed like procedure parameters|
|Used for reusable business operations|	Used for automatic event-based actions|
|Can be executed manually|	Runs when its specified event occurs|
