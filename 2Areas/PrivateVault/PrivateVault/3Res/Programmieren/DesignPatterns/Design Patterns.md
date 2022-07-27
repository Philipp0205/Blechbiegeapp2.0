# Design Patterns
Source: ![[design-patterns-en.pdf]]
Refs: [[!Programmieren]] [[designpatternscard.pdf]]
Tags: #programmieren #design-patterns #software 

---

# Definition
Design patterns are typical solution to commonly oocuring problems in software design. They are like pre-made blue-print that you can customize to sole a recurring desing problem in your code.

# Classification
All patterns can be categorized by ther intent. 
- **Creatioal patterns** provice object creation mechanisms that increase flexibility and reuse of code
- **Structual patterns** explain how to assemble objects and calsses into larger structures while keeping structures flexible and efficient. 
- **Behavioral patterns** take care of effectice communicationd and the assignment of responibilities between objects.

# Features of Good Design
- Code Reuse
- Extensibility

## Design Patters
### Mediator Pattern
#### Problem
Relations between entities can become caotic.
![[MediatorPatternProblem.png]]

#### Solution
The Mediator pattern suggest that you should cease all direct communicatoin between the componente which you want to make indepenend of each other. 
One Class should handle all communicications between the entities. 
![[MediatorPattern.png]]

![[MediatorPatternStructure.png]]

### Factory Method
Is a creatinale deisign pattern that provides an interface for crateing objects in a superclass, but allow subclasses to alter the type of objects that will be crated.

The Factory patterns suggest the you replace direct object constructions calls (using `new` operator) with calls to a special *factory* method. 

#### Structure
![[FactoryPattern.png]]
1. The Product declares the interface, which is common to all
objects that can be produced by the creator and its subclasses.
2. Concrete Products are different implementations of the product
interface.
3. The Creator class declares the factory method that returns
new product objects. It’s important that the return type of this
method matches the product interface.
You can declare the factory method as abstract to force all subclasses
to implement their own versions of the method. As an
alternative, the base factory method can return some default
product type.
4. Concrete Creators override the base factory method so it
returns a different type of product.

#### Example
![[FactoryPatternExample.png]]

# Cheatsheet
![[designpatternscard.pdf]]