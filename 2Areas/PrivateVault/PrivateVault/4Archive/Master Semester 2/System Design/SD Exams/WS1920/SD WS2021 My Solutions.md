# Exam Question 1 "Introduction" 

**In what phase of a project does high flexibility and stability of a design pay off and what is the 
expected gain? (2 Points)**
In the maintenance phase of the project. 
If a design is flexible and stable change can be adopted easily and the system will adapt and survive.

**What would happen in the above phase if a system is not flexible? (2 Points)**
Change is expensive.  The system will stop evolving and die.

## Context and static view 
**Draw the top-level context view with first-level static view as refinement (6 Points)**

![[SD Exam Question ONe.svg]]


**Why is a dynamic view (especially for object-oriented systems) rarely needed? (2 Points)**
The dynamic view show the system as executable units. Usual OO Systems are one big executable unit so this view does not make sense?

*Answer from the QA* 
The advantage of OO is that you first come up with a static view  of the software. 
Focus an static structure of the system. If it is done well enough a dynamic view isn't needed anymore. 

# Question 2 Design Principles 
**What are the consequences of high coupling? (2 Points)** 
- Changes in one element will affect other elements as well. 
- Higher complexity

**What are the consequences of low cohesion? (2 Points)**
- Higher maintenance 
- DRY principle most certainly violated

**How does the class ArrayBasedList translate to Java? Give below the Java-Code for the
class ArrayBasedList which can be deducted directly from the diagram. (3 Points)**

```java
public class ArrayBasedList implements List extends ArraysUtilities {
}
```

**Which design principle is (most likely) hurt by this class? (2 Points)**
- 
- interhitance as specialisatoin?
	- simle arrow to array list 

**What would be the preferred way to model this situation in a correct way (as UML)? (3 Points)**

![[SS20_Question2.svg]]


![[06SoftwareQASummary#UML Arrows]]
**How does the fixed ArrayBasedList translate to Java? (2 Points)**

```java
import java.util.List; 
import app.util;

public class ArrayBasedList implements List {
	private ArraysUtilities arrayUtilities = new ArrayUtilities();
}
```

# Standard Architectures / Architectural Patterns
[[SD Architectural Patterns Lecture]]

**The application is based on three architectural patterns. Name the patterns and give the intentions of these patterns. (6 Points)**

*Model-View-Controller* 
- Application data must be represented from different end user interfaces? 
- Separation of functionality and data from the presentation and control logic. 

*Service oriented architecture* or *Client-Server*
- Reuses legacy app where no common access protocol ist available
- Loosely connected, cross functional and cross platform

*Layered Architecture*
- A layer is an encapsulated unit 
- A layer hides underlying layers, internal complexity 
- Layers communicate

**As noted before, the above architecture contains a problem, fix it: (2 Points)**
Model should not know the view. Only the other way around 

**What would be the Java mechanism, to implement this now fixed pattern? Name it and explain 
its behavior shortly (only textual explanation, no code nLevel 1 Static Vieweeded) (2 Points)**

# Question 4 Reflection
[[SD 04 Reflection Lecture]]

![[WS20_Questoin4_Reflection.svg]]


```java
public class StartUp {
	OperatingSystem os = OperatingSystem.detect();
	System.out.println(os);

	Class<? extends Service> service = null; 
	service = Class.forName(os)

	Client client = new Client(service); 

```

1. Evaluate Annotation wich denotes that there should be something injected. 
2. Looking for the element which has to be injected (eg. properties file, env variable)
3. You know the name of the element that would bei injected 
4. Create object to be injected
5. Assign element to variable 

```java

public class StartUp() {
	OperatingSystem osName = OperatingSystem.detect();
	Class<? extends Service> service =
		Class.forName(osName).asSubClass(Service.class);

	Service service = service.getConstructor().newInstance();g
}
// Evaluate annootatoins 


```


# 5 Parallel Programming 
[[SD Parallel Programming Lecture]]
**This search algorithm should now be redesigned to run in parallel. What is the most fitting 
thread model? (2 Points)**

Most fitting would be the Master/Worker thread model where a central master thread creates multiple worker thread who would search a key. 


**Sketch how you would run this in parallel with the given thread model. Assume 4 kernels to 
run the application. You are free to change the method search in any way and add additional 
fields or do any other changes. You don’t have to repeat the time measurement. You can give 
Java-code (without exception-handling), pseudo-code, pure textual explanation or a mixture of 
al. (8 Points)**

```java
public class Worker {
	private int result;

	public Worker(String name) {
		super();
		this.name = name;
	}

	public int getResult() {
		return result; 
	}

	public void search(int[] a int key) {
		for (int i = 0; i < a.length(); i++) {
			if(a[i] == key) 
				result = i;
		}
		result = -1; 
	}
}
```

```java
public class Master {
	main() {
		int[] toSearch = {...} 		


		// divide array into 4 even parts! 

		Woker w1 = new Woker("Worker 1");
		Woker w2 = new Woker("Worker 2");
		... two more 

		Thread t1 = new Thread(() -> w1.search(toSearch));
		Thread t2 = new Thread(() -> w1.search(toSearch));
		... two more 

		t1.start();		
		t2.start();		
		...

		t1.join();
		t2.join();
		...

	}

}
```

Stop all workers when key is found with global variable.

**What is the overall duration for your algorithm in the best and worst case (again in terms of n
and s)? (2 Points)**

Best case: 
One of the workers find the key at first position -> s 

Worst case: 
All workers have to go through the complete array but one worker finds the key in the last index. 

$d=n/4 \cdot s$


**How could you optimize the behavior of your algorithm (if you haven’t done in the first place) 
to achieve a duration of s for the best case again? Just give a short idea or code snippet. (2 
Points)**
The other threads should check if a solution already has been found 
eg. store the result in one global fields and the other threads check on it. 

**synconizing mechanism**
You don't need it because there is only one writing thread and three are reading

# 6 Reactive Programming
**Use case**
Use case mentioned in the last lecture: 

Stock markets application where one part registers for certain stocks (subscriber) and another parts publishes the new stock data (Publisher).

**What is publisher, subscriber and subscription in your above use case and what are their re-
spective roles? (6 Points)**

*Publisher*
Messages are emitted by a Publisher.

*Subscriber*
Observers messages from a Publisher asynchronously. 

*Subscription*
subscriber receives the Subscription through `onSubscription`.

**Basic features backpressure**
A stream is back-pressured which means a sub only gets as much data as he can handle. Overflowing data is buffered or dopped. 

