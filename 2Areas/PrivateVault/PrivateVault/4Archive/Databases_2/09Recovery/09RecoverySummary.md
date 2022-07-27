# Recovery Summary 
[[chapter9-recovery.e.pdf]]

Logging and Recovery from Software Failures 

## Reading and Writing Data
Reading and writing data from and to DB are not atomic steps but series of steps. 

## Timing of Writing Updates to the DB
Three approaches when updated that transactions has performed on a block of memory are copied to disk. 

1. **Deffered Updates**
Updated are only made after a transaction has committed. 

2. **Immediate Updates**
Updates are written to disk as they happen without waiting for the commit pint of the transaction

3. **Steal/No-Force**
**Steal**: Updated blocks may be written to disk before the transactions commits
**No-Force**: Blocks with transactions updated are not force-written to disk when the transactions commits.

![[StealNoForce.png]]

**Advantage of Steal/No-Force**
The *advantage of steal* is that not so many pages need to be kept in memory to account for pending changes. 
The *advante of no-force*  is that in systems with many transactions operating on the same data, the update block of a committed transaction may still be in memory when a transaction also wants to make changes to it. Then the I/O time to write it to disk can be saved. 

## Logging and Checkpoints 
A **checkpoint** operation, performed periodically, copies log information onto stable storage. The information and operations performed at each checkpoint consists of the following: 
- A *start-of-checkpoint* along with time and date of the checkpoint is written to the log on a stable storage device
- All *log information* from the buffers in the volatile storage is copied to the log on the stable storage. 
- All *database updates* from the buffers in the volatile storage are propagated to the physical database
- A *end-of-checkpoint record* is written and the address of the check-point-record is saved on  a file accessible to the recovery routine on start-up after a system crash. 

Depenendin when the transactions happened and if it was finished a UNDO and a REDO List is created by the recovery routine. 

### Recovery Approaches with Logging

### Checkpoints

### Recovery with Log and Checkpoint

### Recovery with static and fuzzy CPs
Static: 
![[StaticCheckpoints.png]]

Fuzzy: 
![[FuzzeCPsSlides.png]]

## Logging 
Changes to the database are written to a *log file*. 
This file is used during recovery. 

### Write Ahead Logging
If the log is written after the DB update, it is possible that a value changed in the DB but the updated was not logged an thus cannot be undone. 

**Solution:** The information for the log is written before the update to the database. 
**Possible:** The log record an update that was never executed. (Not a problem)

### "Force at Commit" Rule
Log information is written into a buffer in memory first, and not every change may be written to disk immediately. But when a transaction is committed the log buffer is force-written to the disk to ensure that the changes are recorded in the log file. 


## Exam
### SS16 Logging 
![[SS2016Logging.png]]
No, the principles write ahead logging and the *force at commit* rule are violated. 
W1 was written to disk before it was logged. It should be the other way around. 

At the commit pint the *Force at Commit Rule* should be applied and all information from the log-buffer should be written to the log disk.


### SS16 3b)
![[SS16Recovery.png]]
*b)*
1. Load last full backup
2. Load all incremental backups 
3. Load log from backup
4. Start with the current logfile and CPs start with redos

Everything that was either not finished or aborted does not be to redone. Therefore, T1,2,6 do need to be redone because these transactions never happened. 
Only redo the successful transactions. No undo operations needed here. 

### Problem 5 
![[SS16Schedule.png]]
