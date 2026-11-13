# CAP Theorem 
## What is CAP Theorem?
CAP Theorem is a concept used in distributed databases.  
It states that during a network partition, a distributed system must choosen between:  
- Consistency
- Availability  

CAP stands for:  
- C - Consistency
- A - Availability
- P - Partition Tolerance

## 1. Consistency(C)
Consistency means every read receives the latest successful write or an error.  

Example:  
If a bank account balance is updated to ₹5,000, all relevant reads should return ₹5,000 after the update is completed.

## 2. Availability(A)
Availability means every request received by a functioning node gets a response, even if that response may contain older data.  

Example:  
An online shopping application continues responding to users even when some database nodes cannot communicate.

## 3. Partition Tolerance(P)
Partition tolerance means the system continues operating despite communication failures between distributed nodes. 

Example:  
Two database servers cannot communicate because of a network failure.  
The distributed system must handle this situation.

### What does CAP Theorem actually say?
When a networ partition occurs, a distributed database cannot guarentee both perfect consistency and full availability at the same time.  
It must choose one:  

|Type|Meaning|
|---|-----|
|CP|Consistency + Partition tolerance|
|AP| Availability + Partition tolerance|

### CP Database
Prioritizes consistency over availability during network partitions.
- Some requests maybe rejected or delayed.
Example: Certain distributed systems configured for strong consistency.

### AP Database
Prioritizes availability over strong consistency during network partitions.  
- Some requests may return stale data.  
Example: Certain distributed NoSQL systems configured for eventual consistency.

**Note** : CAP does not mean a database permanently chooses only two properties. The trade-off between consistency and availability becomes important specifically when a network partition occurs.
