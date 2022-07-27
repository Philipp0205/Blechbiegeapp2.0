# Learning Goals 
- Understand the area of **Business Rules Management**
- Understand its relation to other BPM areas
- Understand **key tasks** in Business Rules Management
- Model and execute business rules evaluation using Camunda 

# Motivation 
**Environment:** Rapidly changing markets. 
**Problem:** Legacy systems -> process & business logic buried. 
Business depends on devs for system adaptions. 
Changes take too much time.
**Solution:**
- Externalization of processes (BPM)
- Externalization of rules (BRM)
- Direct maintenance of processes and rules by business departments. 

# Terminology 
## Business Rule  
Rule which controls / influences the execution or result of a business process.

Examples 
- Rules for the approval of credit apps
- Price building rules (insurance policies)

## Business Rules Management  (BRM)
- Systematic management of business rules 
- Important aspects: e.g. versioning, access rights management

## BR Management System(BRMS)
A system which supports BRM

## Business Rules Engine
Core of a BRMS for the execution/evaluation of the rules 

## Business Rules Editor 
(Graphical) Editor for business rules

# Rule Types 
- Logical IF-THEN rules 
- Decision Tables / Matrices
- Decision Trees
- Decision / Rule processes
- Complex rule engines a la PROLOG

# BPM, BRM & SOA
Complement each other in an optimal way 

Business Rules can be integrated in Business Processes
- Directly in the business process model (BPM)
- As external service calls (SOA)
- Other ways of integration: Enterprise Application Ingegration, APIs, ... 

# Tools 
- JBoss Drools
	- Web-based BRMS
	- Drools as rule enigne 

# DMN
Decision Model and Notation. 

Describes repeatable decision. 
Can be used for Business Rules? 



