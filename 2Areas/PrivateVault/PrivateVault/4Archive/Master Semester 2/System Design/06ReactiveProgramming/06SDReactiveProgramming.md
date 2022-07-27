
[[SD - 06 - Reactive Programming.pdf]]
[[SD - 06.ex - Exercises (Reactive).pdf]]

# Lambdas / Closures
- Lambdas are effectively 
	- shortcuts for interface-implementations 
	- of interface with a single abstract method
	- without states (i.e. private fields) 
	- without checked exceptions

-> Lambdas allow a less wordy implementation 
-> Lambdas allow passing code to methods

- Closure are more efficient then creating anonymous classes / instances

# Functional Programming
## Basic Idea
- The program is considered as stream of data
- The data is processes by functions 
- Functions have an input and an output but no side-effects

## Streams
- A Stream is a sequence of elements supporting sequential and parallel aggregate operations
- **Lazy evaluation:** The terminal operation triggers the stream. 
- The stream hands over one element after the other to operations 
- Streams cannot preview or undo or restart
- Stream can be considered as Pipes, intermediate operations are Filters

## Intermediate Operations
- .map, .filter, .limit, .peek, etc.

# Reactive Programming 
## Basic idea
- The program is considered as a stream of messages. 
- Messages are emitted by a *publisher*
- A *subscriber* observers the messages asynchronously

The stream is *back-pressured*
- A subscriber gets only as much data as he can handle
- Undelivered data may be buffered or dropped by the publisher.

### Publisher, Subscriber, Subscription
*Publisher* 
- 
*Subscriber*
- Subscriber receives the Subscription through `onSubscription`
- Signals a request through subscription
- May cancel his subscription
- Receives `onNext` with next item, if requested
- Receives `onError`, if an error occurred no further message are available
- Receives `onComplete` when stream is finished
*Subscription*
- Subscriber receives the Subscription through `onSubscription`

## Code 
### Stream creation 
![[Pasted image 20220201134346.png]]

### Intermediate Operations 
![[Pasted image 20220201134406.png]]

