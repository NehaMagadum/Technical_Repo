# ACID 
ACID is a set of four properties that ensure database transactions are processed safely.
ACID stands for:
- A - Atomicity
- C - Consistency
- I - Isolation
- D - Durability

## 1. Atomicity
Atomicity means a transaction is completed entirely or not completed at all.  

It follows principle: All or Nothing.  

Example:   

Bank transfer of ₹1,000 from Account A to Account B.  

Two operations are performed:  
1. Deduct ₹1,000 from Account A.  
2. Add ₹1,000 to Account B.  
If money is deducted from A but adding money to B fails, the entire transaction must be rolled back.
```bash
START TRANSACTION;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```
If any operation fails:
```bash
ROLLBACK;
```

## 2. Consistency
Consistency means a transaction moves the database from one valid state to another valid state.  

All constraints, rules, and relationships must remain satisfied.  

Example:  

- Account balance should not be negative.
- Employee ID must be unique.
- Primary key cannot contain NULL.
- Foreign key must reference a valid record.
```bash
CREATE TABLE accounts (
    account_id INT PRIMARY KEY,
    balance DECIMAL(10,2)
        CHECK (balance >= 0)
);
```
## 3. Isolation
Isolation means multiple transactions executing simultaneously should not interfere incorrectly with each other.  

Example:  

- Transaction A reads an account balance.
- Transaction B updates that balance.
- Transaction A should not observe inconsistent intermediate data.

## 4. Durability
Durability means once a transaction is committed, its changes are permanently saved, even if the system crashes afterward.  

Example:  

After successfully transferring money and receiving COMMIT confirmation, the transaction should remain saved even after a database restart.

### ACID summary
|Property|Meaning|
|-------|-------|
|Atomicity|	All or nothing|
|Consistency|	Valid state maintained|
|Isolation|	Transactions do not interfere incorrectly|
|Durability|	Committed changes remain permanent|
