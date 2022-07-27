# Question 1 - Introduction
**Why should a design be stable? (2 Points)**


**Why should a design be flexible? (2 Points)**
Flexible system can accept change easy and cost efficient and therefore will evolve instead of die.

**Given is the following UML-Diagram. How does it translate to Java?**
```java
public class SpecificPolicy implements Policy {

}

public interface Policy {

}

public class User {
	private Policy policy;
}
```


# Question 2 - Design Principles
**What are the consequences of high coupling? (2 Points)**
Change in one element will affect other elements as well. Will result in cost and time intensive maintenance of system. 
High complexity 

**What are the consequences of low cohesion? (2 Points)**
DRY principle most certainly violated.  
Higher maintenance.

**Which design principle is hurt? (2 Point)**
Inheritance as specialisation 

**What is the correct solution? (4 Points)**
![[Question3InheritanceAsSpec.svg]]

# Question 3 - Architectures

**Sketch a typical three-tier-architecture: name the layer roles and show the direction of usage. 
(3 Points) **



![[Question3LayeredArchitecutre.svg]]

**What are the elements of MVC-Architecture and what are their roles? (3 Points)**

*Model* 
Encapsulates functionality and data from the presentation and control logic.

*View*
Encapsulates representation, remembers state of interaction.

*Controller*
Encapsulates control logic, handles user interaction

**Give a typical use case for a Client/Server-Architecture. (2 Points)**
Complex local business logic / legacy application and server wich provides service.

Use case Email servers are used for sending and receiving emails and clients connect to these servers.

**Give a typical use case for a Service-Oriented-Architecture. (2 Points)**
Reuse legacy app / business process where no common access protocol is available. 

# Question 4 - Reflection 
**Examination Question 4 “Reflection” (10 Points)
What are advantages of using reflection? (2 Points)**
High flexibility

**What are disadvantages of using reflection? (2 Points)**
Complex Code, Risk of runtime problems.

**What is the intention of code injection? (2 Points)**
A system must be able to adapt its structure dynamically during runtime.

**Sketch the execution steps how an application typically injects code with help of Java-
Reflection. You can give Java-code (without Exception-Handling), pseudo-code, pure textual
explanation or a mixture of all. (4 Points)**
![[Pasted image 20220130122925.png]]
# Question 5 - Parallel Programming
**What are goals of parallel programming (in contrast to sequential programming)? (2 Points)**
- To Run programs in shorter period of time 
- To solve with higher accuracy in given time 
- to solve a computational problem at all (eg. size of data) 

**What are the main design tasks when applying the Master/Worker-Model (2 Points)?**
- Divide task into independent segments

Low-Level
- Master creates a Thread for each segment and starts it 
- Master waits with join() for each thread
- If workers access/change shared data use synchronized methods

High-level
- Master creates Executor or ExecutorService
- Assigns Runnable or Callables for each segment
- Retrieves results from Futures 

**What are the main elements of the Producer/Consumer-Model and what are their roles? (2Points)**
- A producer thread sends data into a queue
- A Consumer thread takes the data from a queue

- A producer has to wait if the queue is full 
- A consumer has to wait if the queue is empty 

**Which of the above Producer/Consumer-Elements are threaded, which are synchronized? (2Points)**
The shared data is synchronised the producer and consumers are threaded.

**How is the Pipeline-Model related to Producer/Consumer? (2 Points)**
A Filter is a common Consumer/Producer.

