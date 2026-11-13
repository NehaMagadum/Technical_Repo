# Database Isolation Levels
Isolation levels define how much one transaction is isolated from other concurrent transactions.

Isolation levels help balance:
- Data cosistency.
- Concurrency.
- Performance.

## Problems in Concurrent Transactions
### 1. Dirty Read
A dirty read occurs when one transaction reads data that another transaction has modified but not yet committed.

Example:  
Accounts Table
|account_id|balance|
|---|----|
|1|10000|

Transaction T1 
```bash
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;

START TRANSACTION;

UPDATE Accounts
SET balance = 5000
WHERE account_id = 1;
```
Now T1 has updated the balance to 50000 but has not committed.

Transaction T2
```bash
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;

START TRANSACTION;

SELECT balance
FROM Accounts
WHERE account_id = 1;
```
Output:
|balance|
|---|
|10000|

But T2 already read 50000, which was never committed.This is called dirty read.

### 2. Non-Repeatable Read
A non-repeatable read occurs when a transaction reads the same row twice and gets different values because another transaction updated and committed it.  

Example: 
Employees Table
|emp_id|salary|
|-----|-----|
|1|50000|
 
Transaction A: 
```bash
SELECT salary
FROM Employees
WHERE emp_id = 1;
```
Output:
```
50000
```
Transaction B:
```bash
UPDATE Employees
SET salary = 60000
WHERE emp_id = 1;

COMMIT;
```
Now if Transaction A executes the same SELECT again then the output wiil be:
```bash
SELECT salary
FROM Employees
WHERE emp_id = 1;
```
Output:
```
60000
```

### 3. Phantom Read
A phantom read occurs when a transaction executes the same range query twice and gets a different set of rows because another transaction inserted or deleted matching records.  

Example:  
Transaction A:
```bash
SELECT *
FROM Employees
WHERE salary > 50000;
```
Output:
|emp_id|salary|
|----|-----|
|1|60000|

Transaction B:
```bash
INSERT INTO Employees
Values(2,70000);
```
Output:
|emp_id|salary|
|----|-----|
|1|60000|
|2|70000|

Transaction A executes the same query again.
```bash
SELECT *
FROM Employees
WHERE salary > 50000;
```
Output:
|emp_id|salary|
|----|-----|
|1|60000|
|2|70000|

The additional row is called a phantom row.

## Isolation Levels
### 1. Read Uncommitted
Lowest isolation level.
- Dirty reads possible.
- Non-repeatable reads possible.
- Phantom reads possible.

```bash
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
```
Useful when approximate or less consistent reads are acceptable.

### 2. Read Committed
A transaction reads only committed data.
- Dirty reads prevented.
- Non-repeatable reads possible.
- Phantom reads possible.

```bash
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

### 3. Reapeatable Read
Ensures that repeated reads of the same row remain consistent within the transaction.
- Dirty reads prevented.
- Non-repeatable reads prevented.
- Phantom reads may be possible depending on the database and implementation.

```bash
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

### 4. Serializable
Highest standard isolation level.  
Transactions behave as if they were executed one after another in a serial order.
- Dirty reads prevented.
- Non-repeatable reads prevented.
- Phantom reads prevented.

```bash
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```
It can reduce concurrency and increase transaction conflicts.

### Isolation Levels Comparison

|Isolation Level|	Dirty Read|	Non-Repeatable Read|	Phantom Read|
|------|-----|-----|-----|
|Read Uncommitted|	Possible|	Possible|	Possible|
|Read Committed|	No|	Possible|	Possible|
|Repeatable Read|	No|	No|	Possible in standard behavior|
|Serializable|	No|	No|	No|
