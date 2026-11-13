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
A deadlock occurs when two or more transactions wait indefinitely for locks held by each other.

 Example:
 ```
                         Deadlock Example
              |Transaction AS  |   ->   | Transaction B|
              |  Locks Row 1   |        |  Locks Row 2 |
                 A waits for Row 2; B waits for Row 1
                    Both transactions are waiting !
```

### How to prevent deadlocks?
- Access resources in a consistent order.
- Keep transactions short.
- Avoid unnecessary locks.
- Use appropriate indexes.
- Retry transactions when the database detects a deadlock.
