[[SD - 02 - Design Principles  Methods.pdf]]
[[10DesignPatternsSummary]]

[[SD WS2021 My Solutions#Question 2 Design Principles]]

# Handle Complexity 
*Abstraction* Focuses on the information relevant to a particular purpose and ignores the remainder. 

*Decomposition* A complex problem or system is broken down into parts that are easier to understand. 

# Design Principles
## Encapsulation
- Isolating a system function or a set of data and operations.
- Providing precise specification for the module. 

- -> Make internals private 
- -> Control access through defined public accessors

## Reduced Object Interaction
- Most dependencies are introduced by method calls. 
- -> Objects should only communicate with nieghborhood objects. 
- Reduce Getters/Setters - instead have business functionality. 

## Separation of Concerns / Single Responsibility
- Decomposition according to the responsibility within the system
- Components working on the same task should be grouped (or separated when not) 
- Each unit should only be responsible for one task 

# Interface-Implementation Separation
- Specifications are provided by an interface
- Actual component implements the interface


## Few / Small / Explicit Interfaces
**Few Interfaces** Each unit should have as few connectoins as possible to other units. 

**Small Interfaces** If two units interact, the communications should be as small as possible. 

**Explicit interfaces** If two units interact it should be done explicit. 

## Composition over Inheritance / Inheritance as Specialization
![[Composition over Interitance]]

## Inheritance as Specialization
face-Implementation Separation
- Specifications are provided by an interface
- Actual component implements the interface 

- Inheritance violates encapsulation -> Favor composition over inheritance i.e. delegate calls.
- Use inheritance as "specialisation" never as "Usage".
	- as sub-type -> "is a" modeling 
	- as restriction -> all elements of the subclass are restricted by a condition according to the superclass 
	- as extension -> a subclass introduces new featues, which don't exist in the superclass neither are they applicable to objects of the superclass
- All subclasses of the same level should inherit according to the same criteria -> all are on the same abstraction level.
- Use  single inheritance, avoid using multiple inheritance

![[Pasted image 20220131134938.png]]

## Open/Closed-Principle
![[4Archive/SE2 1/01_Principles/01_Architectural_Principles#Open Closed Principle]]

- **Closed module:** No one is allowed to make changes -> usage without risk 
- **Open module:** Open for extension -> According to new requirements the module can be extended to behave in new and different ways. 

## Substitution-Principle
Any important property of a type should also hold for all its subtypes so that any method written for the type should work equally well on its subtypes. 

-> Each object of a subtype must be aable to substitue an obejct of its usper-type every time. 

# Liskov's Substitution Principle
- Any important property of a type should also hold for all its subtypes so that any method written for the type should work equally well on its subtypes. 

## Dependency Inversion-Principle
![[10DesignPatternsSummary#Dependency Inversion Principle]]

Depend upon Abstractions. Do not depend upon concretions. 

## Interface Segregation-Principle
Interfaces should only provides the methods a client needs. Nothing more. 

If an interface provides too much it should be segreated by several interfaces. 

## Package Principles 
- **The Release Reuse Equivalency Principle** Reusable elements should be released in the granularity of its intended reuse. 
- **The Common Closure Principle**  Classes that change together belong together. 
- **The Common Reuse Principle** Classes that aren't resused together should not be grouped together. 
- **The Acyclic Dependencies Principles**  The dependencies between packages must not form cycles.
- **The Stable Dependencies Principle** Instable components should depend on more stable ones.
- **The Stable Abstractions Principle** Stable packages should be abstract packages 


# Coupling and Cohesion
![[10DesignPatternsSummary#Low Coupling High Cohesion]]

# Design Methods 

## How to start
**Logical Design first** Start with a logical design, do the technical mapping afterwards. 

**Direct mapping** the structure of the design should relate closely to the structures of the problem domain 

**Define a domain model** 
- Precise domain dictionary
- Simplified UML-class diagrams
- Comments describing the behavior 

## How to proceed
*Object-oriented* 
- Homogenous/stable environment
- True real-time-Performance

*Service-oriented* 
- Inhomogeneous / unstable env
- No real-time-Performance
- Cross-company collaborations
- Required platform-independence

*Event-oriented/reactive*
- React on asynchronous events / data streams

### Object-Oriented Design (OOD)
1. Identify Objects/Classes
2. Identify relationships between classes
3. Define interfaces
4. Define functionalities 

### Service-Oriented Design
*Services* 
- Represent a business activity with a specified outcome
- Are self-contained / stateless
- Hide their internals 
- May consit of other underlying services 

### Event Driven / Reactive Design
- Identify events 
- Identify data-streams



