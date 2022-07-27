## Principles
### *Low Coupling / High Cohesion*

*Cohesion*
- the relationship of elements **within** the module. 
- should be as high as possible

-> All elements contribute to one task

*Coupling*
- the relationship between different modules 
- should be as loose as possible 
--- 
-> the module does not depend on other modules 
-> can be changed / exchanged without ripple effects 
-> Less complexity, easier to understand 

### *Open/Closed-Principles*
Open for extension, closed for modification

### *Dependency Inversion Principle*
**Clients**  should only use/depend on interfaces/abstractions
**Details** should be implemented by implementing classes/subclasses

## When to apply
**Observation:** The main work takes place later in the maintenance! 

**Idea:** Forsee future changes already dugin  development: 
- Facilitate expected changes. 
- Prevenent unintentional changes. 

**Pattersn:** Help to avoid dependencies by 
- low coupling (classes are independent)
- high cohesion (calsses focus on an objective)

## Remarks and Risks  
Design patterns support the development of structured and reusable application. 
DPs help to understand foreign programs and support reuse. 

**BUT**
Design Patterns alone do no guarantee project success. 
Design Pattern should not be used compulsively.



## Decorator Pattern 
*(Structural Pattern)*
**Decorator** is a structural pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors. 

- Behavior should be added dynamically to an object.
- The object to be extended is wrapped into decorators
- All calls are delegated through the decorator 
- Each decorator has the change to add his "flavor"

### Structure
![[DecoratorPattern.png]]

## Adapter Pattern
*(Structural Pattern)*
**Adapter** is a structural pattern that allows objects with incompatible interfaces to collaborate.

*Solution*
Create an *adapter*. A special object that converts the interface of one object so that another object can understand it.


### Structure
![[AdapterPattern.png]]

## Composite Pattern 
*(Structural Pattenr)*

*Situation*
Modeling a Part-Whole-Relationship
Parts and composite objects should provide the same interface 

*Solution*
Define a common superclass for primitives and containers. 

### Structure
![[CompositePattern.png]]
![[CompositePatternBook.png]]
