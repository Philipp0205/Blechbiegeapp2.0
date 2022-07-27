[[SD - 03 - Architectural Patterns.pdf]]

[[SD WS2021 My Solutions#Standard Architectures Architectural Patterns]]
# Decomposition
## Layered Architecture
### Usage Scenario
- Stand-alone, monolithic business apps
	
A layer is an **encapsulated unit** 

### A layer hides 
- underlying layers
- internal complexity 

#### Layers communicate
- interfaces, protocols
- top-down

Components within a layer are of similar degree abstraction
- Lower layers mostly focus on technology
- Upper layers rather on the user interface

- Layers may be tested independently and can be exchanged

## Microservices
### Usage Scenario
- **horizontal decoupling** application components
- **independent development** / deployment
- providing a **single functionality** 
![Pasted image 20220117140753.png](app://local/%2Fhome%2Fphilipp%2FDocuments%2F2_Resources_part%2FObsidian%2FObsidian%2F1Projects%2FSemester2%2FSystem%20Design%2F03%20Architecutral%20Patterns%2FPasted%20image%2020220117140753.png?1642424873192)

### Characteristics 
- often applied internally / within a project 
- more fine-grained
- single, lightweight protocol (REST)

# Distribution
## Client/Server-Architecture
### Usage Scenario 
- Remote usage
- Common access protocol available

### Distributed architecture
- **Servers provide specific services** such as printing, data management, 
- clients call on these services
- client access servers through network

### Typical distributes architecture 
- Client / servers are divided into layers too 
	
## Object Request Broker (CORBA)
### Usage Scenario 
- Local/legacy system / complex local business logic
- Remote usage
- **no common access protocol** available

Designed to facilitate the communication of systems that are deployed on divers platforms (for example with different programming langs).

### Distributed architecture
- distributed services
- remote client call these services
- network allows clients to connect servers 
- communication is established by platform-specific object request-brokers (ORBs) 

![[Pasted image 20220121172916.png]]

## Service-Oriented-Architecture
### Usage Scenario
- reuse legacy application / business process—but **no common access protocol** available
- implementation abstraction

### Service
- Implements a business process
- are self-contained / stateless
- is defined by an interface
- is delivered / accessed through a central infrastructure
- remote, synchronous method call though HTTP

But all services have the same DB! Difference to Microservices. 

### Protocols
- Web Services, REST-Services

### Applications using services
- are loosely connected, cross functional and cross-platform
- Simple usage, low performance, low maintainability

## Event-Driven-Architecture
### Usage Scenario
- reaction to asynchronous, outside events 
- single-purpose components processing events 

### Basic set-up
- an outside event is caught
- either triggers a mediator
	- create a set of events  which trigger event processor
- or triggers an event processor 
	- which emits a new, internal event 

Provided high decoupling, but is difficult to control 


![[Pasted image 20220117140825.png]]

# Control Flow
## Centralised Control
#### Usage Scenario 
- Implement control flow through Control Sub-System


### Two variations

*Call-return model*
- sequential top-down subroutine model
- control starts at the top of a subroutine hierarchy and moved downwards

*Manager model*
- concurrent stopping, starting and coordination of other system processes
- sequential loop/switch-statement


![[Pasted image 20220117135738.png]]

## Event Driven Control
### Usage Scenario 
- Implement control flow through Event-Generation and Event-Handling

### **Two Variations**
- *Broadcast model*
	- subsystems register for specific events 
	- an event is broadcasted to all registered subsystem 
	- any subsystem which can handle the event may response 
- *Interrupt-driven model* (for real-time-systems)  
	- Interrupts are detected by an interrupt-handler
	- the interrupt-handler passes the event to some other processing components 

![[Pasted image 20220117140909.png]]


## Reactive (Pipes and Filters) 
### Usage scenario
- **Asynchronous stream of data** to be processed 
- or task can be divided into a **sequence of small processing steps** 

#### Processing step / Processor (Filter) 
- incrementally consumes from its input 
- incrementally produces data to its output 

#### Filters are connected though Pipes 
- consume the output of one filter 
- pipe it to the input of the next filter 

Overall input from some data source 
Overall  output to some data sink, such as a file or display device 

#### Allows 
- no intermediate storage 
- efficient parallel processing 
- flexible exchange and recombination of filters. 
- 
![[Pasted image 20220117140547.png]]

# Interaction
## Model-View-Controller
#### Usage Scenario 
- Application data / functionality must be represented on / triggered from different end user interfaces 

Separation of functionality and data from the presentation and control logic
- Model encapsulated Access to Functionality and data 
- view encapsulates Representations , remembers the state of interaction 
- Controller encapsulated Controller logic, handled user interaction 

#### Event-Driven-Control
- a view is registered at a model
- the controller calls the model for executing the selected action
- a model emits an event for the view should be updated, which is caught by registered views. 

![[Pasted image 20220117140623.png]]

## The Repository Model
#### Usage Scenario
- Several systems share a data source 
- but won't be bothered with the current db-details 

#### Abstract Database-Model
- Provides access to common data 
- accessed by all sub-system
- allows centralised management 
- but all systems must agree on a repo data model -> inevitably a compromise  

![[Pasted image 20220117140652.png]]

## Active Records 
#### Usage Scenario
- Simple transition from objects and db-data

The Repository Model warps a complete database - Active records instead: 
- one Active Record-Class maps to one Table
- one Active Record Object maps to one Table-Row
- each active record has its own methods for save, retrieve
- save/retrieve is attached to the objects -> spearations of concers
- typically a framework is needed 
- yields more complicated / interwoven code 


## Microkernel / Plugin-Architecture
### Usage Scenario 
Product which should be extendable by future functionality 

#### Microkernel
- is a **minimal** core with **basic logic** / workflow, provides core functionality accessible thorough a microkernel-interface

#### Plugins
- implement additional, specific functionality
- access the microkernel-interface
- are separated. 