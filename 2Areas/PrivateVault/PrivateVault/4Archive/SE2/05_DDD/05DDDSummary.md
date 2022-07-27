# Cheat Sheet 
[[SWE2-DDD-new.pdf]]
DDD is an approach to building software with a focus on the domain. 

## Domain Model 
Should represent vocabulary and the key concepts of the problem domain. Identifies relationship among all entities in the scope of the domain. 



---
Business delimited data. 
Elements of the context are motivated exclusively by business aspects. 

# Important Terms 
*Domain*
Sphere of knowledge, influence or activity. The subject to which the user applies software. 

*Model*
System of abstractions that describes selected aspects of a domain. 
Used to solve problems. 

The *Domain* is the world of the business, the *Model* is your solution and the *Domain Model* is the structured knowledge of the problem.

*Ubiquitous Language*
Language structured around the domain model. Used by all team members  within a bounded context to connect all the activities of the team with the software. 

*Context*
The **setting** in which a word or statement appears that determins the meaning.

*Bounded Context* 
Boundary that surround a particular model. This keeps the knowledge inside the boundary consist whilst ignoring noise from the outside world. 

*Event*
Something that has happened in the past. 

*Domain Event*
Something that happend in a particular domain.


# Tools

**Context Map**
A *Context Map* is the global view of the application as a whole. Each Bounded Context fits within the Context Map to show how they should communicate among each other and how data should be shared. 

---
Each domain or subdomain has a bounded context. On this basis, a context map is created. Contexts can have dependencies to each other. 

*Context Mapping* is the strategy of how a context is integrated into another. Context mapping brings organizational aspects to the fore and describes applicable patterns. 

**Implementation possibilities of Context Mapping** 
*Recommended*
- Restful API, Webservicess,Messagingg with domain events 

*Possible*
- Integrationn through libraries in an automatedenvironmentt

*Antipattern* 
- Database Integration. In this case it is essential to use the Anticorruption Layer, Open Hostservicee and Published Language. 

# General 

# Exercise 
Sub domains 
- User management
	- ![[4Archive/SE2/05_DDD/Pasted image 20210412161950.png]]
	- ![[4Archive/SE2/05_DDD/Pasted image 20210412170809.png]]
	
---
#cheat-sheet/se2