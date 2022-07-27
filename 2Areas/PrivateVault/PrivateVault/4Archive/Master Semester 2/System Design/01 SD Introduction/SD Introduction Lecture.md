[[SD WS2021 My Solutions#Exam Question 1 Introduction]]
[[SD - 01 - Introduction Initial Steps.pdf]]

# Definitions
## Design 
The process of **defining** the **software architecture, components, modules, interfaces** and **data**. 

## Logical Design 
An **abstract representations** of the **data flows, inputs** and **outputs** of the system. 

## Physical design 
Actual **input and output processes** of the system. 

## Architecture 
The **structure** of the system, which consist of **software elements** and their **external visible properties elements** and the **relationships** among them.

## Structure
- The sum of relationships between its entities which stay invariant.
- A software architecture maybe defined by several structures (views)  

# Dilemmas
Structures are stable vs. Requirements are volatile.

Structures try to absorb requirements vs. Requirements try to shake structures. 

Architecture should provide **stability** and **flexibility** 
- If a design is good, change can be adopted easily
	- -> the system will adapt and survive
- If a design is bad change is expensive
	- -> the system will stop to evolve and die 

## Why should a design be stable 
- Foundation for the entire system 
- Without it balancing implementation, testing and maintenance will get difficult. 

## Why should a design be flexible
- Change can be adopted easily
- System adapts and survives 


# SD Design Phases
Business Process analysis -> Requirements Specification -> Design  -> 
Implementation -> Verification and Validation -> Maintenance

# Initial Design Steps 

## Major Tasks and Domain elements 
Describe the major tasks. 
- Two or three positive sentences
- Use domain terms 
- List the fice most important domain terms 

## Usage and Users 
What type of usage should be achieved? 
- *Interactive & operational* -> transform current data, highly available and performance (CRUD)
- *decision support*  -> read/evaluate current data, lover available performance
- *batch* -> pre- or post-processing, interaction with other systems.
- *embedded* -> hardware integration
- *real-time* -> guaranteed exec time s 

Stakeholders
- Users of the system and their roles 
- Negative stakeholders

## User interfaces, System interfaces
User interfaces 
- form based / object-oriented / command-line / special devices
- adaptable to experience / user groups
- installer / user 

System interfaces
- to / from other systems
- data-interface
- functional interface: synchronous / asynchronous, definition, fault-tolerance

## Data access and organisation
Storing data in 
- main memory
- files 
- db

## System control 
Ways to control the system
- procedural
- event driven /reactive
- parallel
- rule-based

## Views 
### Context View
- System is a **black box** 
- Is connected to the environments
	- other systems
	- users
- Notation: **package-diagram** like notation

### Static View
- System is seen as **related components**
- Components (packages, classes, modules, tables, functions, libs)
	- may use each other within one level
	- may be refined hierarchically into lower levels 
- Notation: **Simple Class- / Package Diagram** 

### Dynamic View
- The system is seen as executable units 
	- may transfer control
	- may transfer data
- Notation: **Sequence Diagrams**

Optional: 
- *Deployment View*
- *Data View

## Exam question 
In what phase does high flexibility and stability of a design pay of?

- Throughout lifecycle, but it pays of exponentially. 
- System is flexible and stable, change  can be adopted easily. 
- System will survive .


# Questions
- Difference Context View and Static View and SV Level 1 and 2 

