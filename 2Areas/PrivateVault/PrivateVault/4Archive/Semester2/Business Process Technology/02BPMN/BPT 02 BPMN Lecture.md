[[02BPMNSlides.pdf]]
[[BPTExcercise1.pdf]]

# Learning Goals 
- Understand background of BPMN
- Decide on the appropriate BPMN model type for modeling
- Model example business processes with the given constructs
- Motivate and create company modeling conventions

# Naming 
### Processes and Activities 
- VERB, NOUN
- Consistency check: Rephrase to result. NOUN, VERB
- *Create customer order* -> *Customer order created* 

## Events 
- At the end of process or activity state (NOUN, VERB) should be reached. 
- *Drink beverage* -> *Beverage drunk* or  *Drink beverage* -> *Thirst quenched *

# Modeling Steps 
## 1. Collect Material 
Sources
- Sources
- Documents
- Interviews
- Workshops
- Observation
- Benchmarking

Types 
- Things (what)
- Facts about things
- Metrics
- Roles (who)
- Activities (how)
- Processing methods (how)
- Information methods
- Other

### Process environment
![[Pasted image 20220203104229.png]]

- Process design 
- IT
- Environment

- Motivation
- Organisation 
- Rules & Policies 

## 2. Clarify Terminology 
- Use same term in different parts for the process.
- Agree on terminology 

## 3. Define Process boundaries 
- Are that multiple processes or one? 
- Important criteria: How many tokens are there? If it's only one it might be only one process as well 

 - All activites processes 1 Token
 - Trigger event beyond process control 
	 - eg customer 
 - End event of the Happy Path leaves >=1 stakeholder happy 
 - Process name: Noun + active verb derived from process result
 
## 4. Define Basic activities 
- 

## 5. Trigger, Results, Activities 
- Add triggers, results, activities and cases to process. 

## 6. Refinements 
Common Refinements

1. Split
2. Merge
3. Exception handling
4. Waiting time
5. Interrupt handling
6. Interaction with external stakeholders
7. Responsibilities
8. Data Input/Output
9. Related data records & documents
10. Outcome-oriented

# BPMN
## Model types 
### Private Business Processes 
- Internal Processes
- Private non-executable (internal) BP
	- Factual modeling without executability goal 
- Private executable (internal) BP
	- Contain all necessary information for exection
	
### Public Processes 
- Represent the interactions between a private process another processes or participants
- Only communicating activities considered
- External communication via messages

### Collaborations 
- Interaction between different orgas/participants in multiple pools 
- Communication via messages. 

### Conversations 
-  „Aggregated“ view on
- communication between entities
- No execution order

### Choreographies 
- Interaction-oriented representation between multiple entities
- Typically no pools

## Model elements 
![[Pasted image 20220203113028.png]]
## Modeling Rules
- Pools & Lanes
	- Separate Pools for orgas 
	- Lanes for departments/roles/systes
- Message & Sequence Flows
	- *Message Flows* between Pools
	- *Sequence Flows* inside a Pool
	- Catch messages with Receiving Start- or Intermediate Event
	- Messages typically carry a Data Object
- Sequence Flows with Start- and End-Events
	- Connect all elements of every Pool with a closed sequence of Sequence Flows to a Start- and at least one End-Event

## BPM Tips from prof 
- No sequence flow between pools, only message events. 
