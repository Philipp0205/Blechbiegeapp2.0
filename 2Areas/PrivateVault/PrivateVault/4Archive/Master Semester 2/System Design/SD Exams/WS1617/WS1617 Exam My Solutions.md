# Question 2 - Initial Vision
## Major tasks and Domain Elements
- The systems manages grocery **items** and ships them to the customer at an agreed **delivery time**
- Items can be scanned with **bar code** or **QR Code**
- A **companion app** manages the **shopping list** gives recommendations based **cross selling** advice already bought items.
- The app should also manage the **stock** and **packing lists** for employees.

Domain terms: 
- items
- delivery time 
- bar code / QR code
- Shopping list 
- stock 
- packing list

## Additional Steps 
### Usage and Users 
The usage is interactive & operational because the users perform CRUD calls on the servers. 

The users are: 
- Admin
- Customer (busy groceries)
- Employee (packs groceries)

No negative stakeholder

### User Interface and System interfaces 
User interface is form based, object oriented
Interfaces to other systems are 

System interfaces to user database and store server. Async interface. 

### Data Access and Organization 
Stores shopping list local in files. 
Already bought items are stored in database. 

### System Control
Event driven/reactive / Systems reacts to graphical user interfaces

## Static top level view & level 1 view
![[Q2 ContextView Static View.svg]]

# Question 3 - Design Principles
**What are the two different ways to “read” the inheritance relationship in an UML-Diagram?**
*Inheritance as*
Specialization

*Inheritance as*
Usage

**What is the problem of having these two different interpretations?**
All subclasses of the same level should inherit according to the same criteria -> all are on the same abstraction level.

**Which one is the preferred one?**
**How should the rejected interpretation be represented instead in UML? (Name it or draw it)**
Inheritance as spcialization.

**How should the rejected interpretation be represented instead in UML? (Name it or draw it)**

![[InheritanceAsSpecialization.svg]]


# Question 4 - Coupling & Cohesion
**Examination Question 4 “Coupling and Cohesion” (8 Points)
What degree of coupling and cohesion is desired (Tick the right answer) and why? What**
...

