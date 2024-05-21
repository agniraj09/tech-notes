Transaction Propagation
---
Transaction Propagation defines how transactions relate to each other. It outlines rules for managing transactions when one method(which is already in a transaction) calls an other method(which is also transactional).

Types
---
1. PROPAGATION_MANDATORY
> An active transaction is required to execute the method or business logic. If an active transaction exists currently, spring will use it, else spring will throw an exception.
2. PROPAGATION_REQUIRED - default
> If an active transaction exits currently, spring will use it, else spring will create a new transaction.
3. PROPAGATION_SUPPORTS
> If an active transaction exits currently, spring will use it, else the method/logic will be executed without transaction.
4. PROPAGATION_NEVER
> Method or logic needs to be executed non-transactionally. Spring will throw an exception if an active transaction exists currently.
5. PROPAGATION_NOT_SUPPORTED
> If an active transaction exits currently, spring first suspends it then executes the method/logic.
6. PROPAGATION_REQUIRES_NEW
> Spring suspends current transaction and always creates a new one.
7. PROPAGATION_NESTED
> Spring will keep the current active transaction as is and creates a new transaction to exeucte the method/logic and the new one will be closed once inner logic is executed.


Transaction Isolation
---
Transaction isolation refers to the degree to which one transaction is isolated from other transactions which are running concurrently. It's about controlling how and when changes in one transaction is visible to each other. Before diving deep to the types, we need to know about below concepts,\
&ensp; **Dirty Reads** : Reading uncommitted data which may be rolled back in future.\
&ensp; **Phantom Reads** : When a range of rows are selected with some condition and another transaction inserts a new row in the range and hence read results differ for each read.\
&ensp; **Non-repeatable Reads** : When a row is retrieved twice in a transaction and the values in the row differ between reads due to changes to the row in other transaction.

Types
---
1. READ_UNCOMMITTED
> This is the lowest level of isolation. This means, uncommitted changes of a transaction are visible to other transactions. This results is dirt reads and hence not recommended. Not supported in Postgres, Oracle.
2. READ_COMMITTED
> This is the next level of isolation. Only committed changes are visible to concurrent transactions. This avoid dirty read but still does not overcome phantom and non-repeatable read.
> This is the default isolation level in Postgres
3. REPETABLE_READ
> It prevents non-repeatable reads. How is it done is, it basically puts a lock on all rows or data read by the transaction and does not allow other transactions to modify it. But still it does not overcome phantom reads.
4. SERIALIZABLE
> This is the highest level of isolation. Basically it executes all operations in a serial manner and hence no concurrent changes are made. This might result in bad performance.
5. DEFAULT
> Default isolation level supported by RDBMS
