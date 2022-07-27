# Concurrency Summary 
[[chapter8-concurrency.e.pdf]]

## Isolation 
### Dirty-reads problem
Occurs when one transaction is allowed to see the intermedia results of another transactions before it has committed. 

### Lost update problem 


## Serializability and Recoverability 
## Locking 
**Exclusive Lock:** By default, SQL Server sets an exclusive lock for data that is being modified to ensure data consistency until the transaction is complete. 

**Deadlock:** An impasse that may result when two (or more) transactions are each waiting for locks to be released that are held by the other.


### Two-phase-locking (2PL)
A transaction follows the two-phase locking protocol if all locking operations precede the first inlock operation in the transaction. 

According to the rules of this protocol, every transaction can be divided into two phases: first a *growing phase*, in which it acquires all the locks needed but cannot release any locks, and then a *shrinking phase*, in which it releases its locks but cannot acquire any new locks.

### Optimistic Protocols 
**Assumption for applying optimistic Protocols:** Conflicts only occur rarely. 
Under this assumption, it is more efficient to restart a transaction in case of a conflict than to prevent conflicts from happening in the first place. 

## Isolation Levels
![[IsolationLevels.png]]
**Isolation Level:** Degree of interaction that is allowed from other transactions during the execution of a transaction. 

1. **Read Uncommitted:** is the lowest isolation level. One transaction may read not yet committed changed made by an other transaction.
2. **Read Committed:** Data which is read is committed at the moments of the read. 
3. **Repeatable Read:** Most restrictive. Transactions holds read locks on all rows it references and write locks on all row it changes. Since other truncation cannot change rows it avoids non-repeatable read. 
4. **Serializable:** Highests isolationn level. Transaction are serially executed.

Only *Serializable* is safe because it generates serializable schedules. 

Serializability isn't always used because it is slower when you have to wait for operations from one transaction finish before the next begins.  
  
A repeatable read guarantees that data which is read can not change, so this would be useful for banking application, for example, when a customer opens their account (locking upon read) until the time that they close the transaction (unlocking)

When a repeatable read exists one must accept the possibility of a phantom read. 

## Exercise from the Lecture 
![[ConcurrencyExercise.png]]
![[ConcurrencyExerciseChoices.png]]

1. Correct because TB is already reading the salary value, and therefore it is locked.
2. No because TA is blocked until TB is committed or aborted.

3. No TA is blocked since step 6, TB can run normally.
4. No because only B hold the lock A is waiting for. Therefore, we have no deadlock.
5. Wrong because the lock don't block other read reads, only writes. The taSalray is read-locked because it is used by TB in step 4. So TA actually can read from the taSalary table. 
6. No true because A can not continue with and therefore did not update the value in the meantime.
7. As seen in the *appendix* the value is read. 
8. Transaction a is locked until TB it is committed or aborted. In a serializable schedule the outcomes should be the same every time.
9. Yes that is correct.
10. Yes if B takes to long A could have a time out.

