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
