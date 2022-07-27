#lecture-note |  #t

---

# Transactions Summary 

## ACID vs. BASE
The **CAP theorem** states that it is impossible to achieve both *consistency* and *availability* in a partition tolerant distributed system. 

*ACID* and *BASE* deal different with this limitation. 

- The ACID model provides a consistent system. 
- The BASE model provides high availability. 

**ACID**
- **Atomicity:** Either all operations of a transaction are executed or none. 
- **Consistency:** A transaction must transform the database from a consistent state to a consistent state. 
- **Isolation:** Only after successful competition, partial results of a transaction may be released. 
- **Durability:** After the successful termination of a transaction, its results are persistent, they can only be changes or undone by a new transaction 


**BASE**
- **Basically Available:** At all times, data is locally available, but not necessarily all of the data. 
- **Soft state:** 
- **Eventually Consistentt:** Whenassessedd at a random time, not all of the different sites involved in a distributedtransactionn may have a consistent outcome, but at some unknown point of time in the future, consistency will definitly have been achieved.

SQL databases are almost uniformly ACID compliant. 
NoSQL databases tend to conform to BASE principles.

ACID-compliant DBs will be a better fit for those who require consistency, predictability and reliability. 

Those who consider growth to be among their priorities will likely want to choose the BASE model, because it enables easier scaling up and provides more flexibility. 

