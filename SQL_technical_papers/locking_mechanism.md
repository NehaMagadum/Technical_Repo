# Locking Mechanism
- Locking is a mechanism used by databases to control concurrent access to data.  
- It prevents multiple transactions from modifying the same data incorrectly.

Example:
- Two users try to update the same bank account simultaneously.
- Locking helps maintain data consistency.

## Types of Locks
### 1. Shared Lock(S Lock)
A shared lock is used for reading data.
- Multiple transactions can hold shared locks simultaneously.
- Other transactions can usually read the same data.
- Writing is blocked while incompatible shared locks are held.

Example:

- Transaction A reads an employee record.
- Transaction B can also read it.

But Transaction B may not be able to update it until conflicting locks are released.

### 2. Exclusive Lock(X Lock)
An exclusive lock is used when modifying data.
- Only one transaction can hold the exclusive lock on the same resource.
- Other transactions cannot obtain conflicting read or write locks.
- It protects data during modification.

Example:

- Transaction A updates employee salary.
- Transaction B cannot simultaneously update the same locked record.

### Lock Granularity
Lock granularity means the size of the database resource being locked.
|Type	|Meaning|
|------|-------|
|Row-level|	Locks individual rows|
|Page-level	|Locks a page of records|
|Table-level|	Locks an entire table|
|Database-level	|Locks the entire database|

### Row-level locking
Locks only the required row.

**Advantages:**
- Better concurrency.
- Other rows can be accessed simultaneously.

### Table-level locking
Locks the entire table.

**Advantages:**
- Simpler lock management.
- Useful for certain bulk operations.

**Disadvantages:**
- Reduces concurrency.


## Deadlock
- A deadlock is a situation in a database where two or more transactions are waiting for resources locked by each other, and none of them can proceed.
- In simple words, transactions keep waiting for each other to release locks, but nobody releases their lock.
- A deadlock causes transactions to stop making progress until the database resolves it.

 **Example1:**
 ```
                         Deadlock Example
                |Transaction A|   ->   |Transaction B|
                 |Locks Row 1|          |Locks Row 2|
                 A waits for Row 2; B waits for Row 1
                    Both transactions are waiting !
```

**Example2:**  
Consider two database transactions:
- Transaction T1
- Transaction T2  

And two database records:  
- Record A
- Record B

**Step-by-step execution**
|Step|	Transaction T1|	Transaction T2|
|------|------|-------|
|1|	Locks Record A|	  |
|2	|	     |Locks Record B|
|3	|Requests Record B|   |	
|4|		|Requests Record A|
|5|	Waits for T2|	Waits for T1|

Now:
- T1 holds a lock on A and waits for B.
- T2 holds a lock on B and waits for A.
- T1 cannot proceed until T2 releases B.
- T2 cannot proceed until T1 releases A.  

Therefore, both transactions are waiting indefinitely.This situation is called Deadlock.

### SQL example of Deadlock
Consider an 'Accounts' table.
|account_id|balance|
|-----|-----|
|1|10000|
|2|20000|

**Transaction T1**
```bash
START TRANSACTION;

UPDATE Accounts
SET balance = balance - 1000
WHERE account_id = 1;
```
T1 locks account 1.

**Transaction T2**
```bash
START TRANSACTION;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 2;
```
T2 locks account 2.

**Now T1 executes**
```bash
UPDATE Accounts
SET balance = balance + 1000
WHERE account_id = 2;
```
T1 waits because T2 holds the lock on account 2.

**Now T2 executes**
```bash
UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 1;
```
T2 waits because T1 holds the lock on account 1.

- Now both transactions are waiting for each other.

### Four Necessary Conditions for deadlock
Deadlock occurs when all four conditions exist simultaneously.  

**1. Mutual Exclusion**  
A resource can be held by only one transaction at a time when an exclusive lock is required.    
**Example**: T1 holds an exclusive lock on Account A.  

**2. Hold and Wait**    
A transaction holds one resource and waits for another resource.  
**Example:** T1 holds Account A and waits for Account B.  

**3. No Preemption**    
A resource cannot be forcibly taken away from a transaction. It must be released voluntarily or through transaction rollback.  
**Example:** T2 cannot simply take Account A's exclusive lock   from T1.    

**4. Circular Wait**  
Transactions form a circular chain of waiting.  
**Example:**  
- T1 waits for T2.
- T2 waits for T1.

### Deadlock Handling Techniques
**A. Deadlock Prevention**  
Deadlock prevention means designing the system so that at least one of the four necessary conditions cannot occur.  
Examples:  
- Avoid hold and wait by requesting all required locks together.
- Prevent circular wait by acquiring locks in a fixed order.
- Use appropriate resource allocation policies.  

Example:  
Always lock Account A before Account B.  

Both transactions follow the same order:  
```
Account A → Account B
```
This prevents circular waiting between these accounts.

**B. Deadlock Avoidance**  
- Deadlock avoidance checks whether granting a resource request will keep the system in a safe state.  
- If granting a request could lead to an unsafe state, the system delays the request.  
An example algorithm is:  
**Banker's Algorithm**  
It checks whether resource allocation can safely allow all processes to complete.  

**C. Deadlock Detection and Recovery**  
The database allows deadlocks to occur, detects them, and resolves them.  
- A common technique is a Wait-for Graph.  
- If the graph contains a cycle, a deadlock exists in the corresponding single-instance resource model.

Example:  
```
T1 → T2
T2 → T1
```
his indicates deadlock.  

**Recovery**  

Once detected, the database can:
- Abort one transaction.
- Roll back one transaction.
- Release its locks.
- Allow the other transaction to continue.  

The aborted transaction may be retried later.

### How MySQL Handles Deadlocks
- Transactions acquire locks during operations.
- InnoDB detects deadlocks automatically.
- It selects one transaction as the victim.
- The victim transaction is rolled back.
- Its locks are released.
- The other transaction continues.

### How to prevent deadlocks?
- Access resources in a consistent order.
- Keep transactions short.
- Avoid unnecessary locks.
- Use appropriate indexes.
- Retry transactions when the database detects a deadlock.
