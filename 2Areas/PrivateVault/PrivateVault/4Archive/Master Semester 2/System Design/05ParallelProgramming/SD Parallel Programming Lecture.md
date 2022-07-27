[[SD05ParallelProgrammingLectureb.pdf]]

# Parallel Programming 
# Laws
- Amdahl's Law
	- Fixed problem size 
	- Overly pessimistic
	- states that the possibilities are very limited 
- Gustafson's Law
	- Fixed problem time
	- overly optimistic 
	- states that the possibilities are nearly linear

The truth is somewhere in the middle. 

## Motivation
- To Run programs in shorter period of time 
- To solve with higher accuracy in given time 
- to solve a computational problem at all (eg. size of data) 

# Threads in Java

## High-level creation 
- Create Executor and supply a Runnable 
- Create ExecutorService and supply a Callalbe

(nicht so relevant denke ich)

## Requirements
*Concurrency* 
- multiple tasks can be done at the same time 
*Scalability*
- if tasks are dependent on each other there should be **little communication and synchronization**
*Locality*
- if data is exchanged it should be done rarely

# Processes and Threads 
*Processes*
- separated and isolated tasks with different memory 
- heavy-weight, difficult communication

*Threads*
- independent tasks sharing memory and working on common data
- light-weight, easy communication

## Low-Level-Control of Threads
- start / (stop)
- wait / release
- suspend/resume

- synchronized
	- a caller entering this method locks the whole object
	- all other callers trying to access any other synchronized parts of this object have to wait
	- the lock is released when the caller leaves the method or  calls wait()

## Java
## Direct creation 
- Implement a Runnable and start it through a Thread 
- Supply a lambda-expression 

### With Runnable Class
![[Pasted image 20220131153348.png]]
```java
public class Target implements Runnable {
	public void run() {
		// do something in parallel
	}	
}
```

```java
Target target = new Target();
Thread myThread = ne Thread(target);
myThread.start();
```

### With Lambda

![[Pasted image 20220131153402.png]]

```java
public void doSomething() {
	// do something in parallel
}

...

Thread myThread = new Thread(() -> doSomething());
myThread.start();
```

## High-level creation
### Executors
Setting up a Thread-Pool with a fixed number of threads. 

```java
Executor executor = Executors.newFixedThreadPool(3);
```

Define and starting Threads
```java
List<Runnable> runnables = ... 
for (Runnable runnable : runnables) 
	executor.execute(runnable);
```

### Executor-Services
```java
// Setting up a Thread-Pool
ExecutorService executor = Executors.newCachedThreadPool();

// Defining and staring the Threads
Callable<Type> callable = () -> returnSomeType();

// Future is a result available later, when the thread is finished 
future<Type> future = executor.submit(callable); 

// Accessing the result 
futur.isDone() // true when result is avialable 
Type value = future.get(); // blocks until the result is available

// Stopping the Threads
executr.shutdown();
```


### Master/Worker
*Delegation or Master/Worker*
- Central Master-Thread creates Worker-Threads
- Master assigns each worker tasks
- Master may wait until workers complete
---

- Divide task into independent segments

Low-Level
- Master creates a Thread for each segment and starts it 
- Master assigns tasks for each worker
- Master waits with join() for each thread
- If workers access/change shared data use synchronized methods

High-level
- Master creates Executor or ExecutorService
- Assigns Runnable or Callables for each segment
- Retrieves results from Futures 

```java
public class Worker {
	private String name;
	private int result;

	public Worker(String name) {
		super();
		this.name = name;
	}

	public int getResult() {
		return result;
	}

	public void doSomething(int n) {
		result = 0;
		while(n > 0) {
			System.out.println(name);
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			n--;
			result++;
		}
}
}
```


```java
public class Master {
	public static void main(String[] args) throws InterruptedException {
		Worker w1 = new Worker("Worker 1");
		Worker w2 = new Worker("Worker 2");

		Thread t1 = new Thread(() -> w1.doSomething(5));
		Thread t2 = new Thread(() -> w2.doSomething(10));

		t1.start();
		t2.start();
		t1.join();
		t2.join();

		System.out.println("Result 1: " + w1.getResult());
		System.out.println("Result 2: " + w2.getResult());
	}
}
```


### Consumer/Producer
*Producer-Consumer*
- Producer-Threads produce data
- Data is stored in shared memory 
- Consumer-Threads consume the data 
--- 
- A producer thread sends data into a queue
- A Consumer thread takes the data from a queue
- A producer has to wait if the queue is full 
- A consumer has to wait if the queue is empty 

![[consumer1.png]]

![[consumer2.png]]

![[consumer3.png]]
![[Pasted image 20220131160846.png]]


### Pipeline 
- Processing is done in several stages 
- Each stage is Filter-Thread that performs work on a unit of input

- A Pipe is a queue with synchronized access
- A Filter is a common Consumer/Producer with 
	- its own thread
	- an assigned input queue from which he consumes 
	- an assigned output queue to which he produces 

![[pipeline1.png]]
![[pipeline2.png]]
![[pipeline3.png]]

### Peer-to-Peer (not relevant)
- Mixture of the previous use-cases
- Peer-Thread have equal status and act on their own 
- Working on shared data or private data