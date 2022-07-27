---
type: cheat-sheet
lecture: SE2
tags: lecture/se2
---

[[SWE2-MDSD-new.pdf]]
[[SE2Exams]]

# Summary 
## Xtext and Xtend 
*Xtext*
Xtext is an open-source software framework for developing programming languages and DSLs.

*Xtend*
Dialect of Java that compiles into readable Java source code. 

## MDA 
There are three models in MDA. All three models may conists of one or more UML diagrams.

*Computation-Independent Model (CIM)*
Combines the requirements and domain models. It models the system in terms of how it will interact with its environment. 

*Platform-Independent Model (PIM)*
The design model. It describes the internal structure of the model without regard to the hosting platform. 

*Platform-Specific Model (PSM)*
The implementation model. It add concepts from the hosting platform to the hosting platform. 

*UML profiles*
UML profiles are the standard mechanism for expanding the vocabulary of UML.

## Comparison GPLs and DSLs
![[GPLsvsDSLs.png]]


# Lecture Notes (outdated)
## Domain Specific Languages 
### GPLs vs DSLs 
- ![[GPLvsDSL.png]]
	
### Internal vs External  
- internal 
	- A DSL implemented on top of an underlying programming language is called an internal DSL, embedded withing the language that implements it 
	- Uses infrastructure of the host 
	- eg. Gradle based on Groovy 
- External 
		- A DSL designed as an independent language without using the infrastructure of an existing host language is called an external DSL
			- Own syntax, semantics and language infrastructure implemented separately by the designer 
### Advantages and Disadvantages of using a DSL 
- Adv
	- Easier collaboration with business users 
	- Better expressiveness in domain rules 
	- Concise surface area of DSL-based APIs
	- DSL-based development can scale 
- Dis
	- Project can end up as complete mess by using badly designed DSL 
	- DSL design is for experts 
	- Up-front cost 
	- A tendency to use multiple languages 

## Model Driven Architecture (MDA)
### Def 
- Consists our of 3 rings
	- MDS kernel integrates the standards 
	- the next ring of MDA contians all platforms and techniques that are necessary for the execution of the application 
	
### Meta Model
- ![[MetaModelExample.png]]
- ![[MetaModelWithMoreComponentsFromLecture.png]]

### Motivation and Requirements for MDSD
- XMI



### todo 
- modeling language 
- metamodel
-  model editor 
- generator / interpret
- tools for creating metamodel, editor , transformator 

# Exam
- What are internal and external DSLs? 
- Within the xtext exercise you had two roles "Tool Builder" and "Tool User". Describe shortly what were the main tasks and outcomes in these two roles ?
- What are the advantages of a DSL compared to a GPL 