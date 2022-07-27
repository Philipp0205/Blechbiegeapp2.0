---
type: cheat-sheet
lecture: SE2
tags: lecture/se2
---

# Principles Cheatsheet 
[[SWE2-ArchitecturalPrinciples-new.pdf]]

## Value System
*Evolvability*
Software must have an internal structure that favors changes of that software.
Ideally, the implementation of a features costs a fixed amount. 
The simpler a software can be adapted, the higher it evolvability is.

*Correctness*
Must be considered during the development. 
Developers have to deal with the issue of correctness. Clear requirements and acceptance criteria are needed. 

*Production Efficiency*
Development time and the price of the software is an important aspect. The price is higher with inefficient production.
High production-efficiency means that software can be developed further for years or even decades. 

*Reflection*
Without no further development is possible. It is important to always consider new findings. 
Reflection needed on all levels: Pair programming, reviews, daily, iteration, entire industry. 

## Principles 
*Don't repeat yourself (DRY)*
Reduce repetition of information of all kinds. 
Single source of truth. 
Implement and maintian functionality only once. 

*YAGNI (You ain't gonna need it)*
Functionality that is implemented in advance *costs time, is not tested*, makes code *complicated*, will never be *used*. 

*Keep it Short and Simple (KISS)*
Perfect doesn't mean that you *cannot add something* it does mean you *cannot remove something*. 

*Principle of least astonishment*
A component of a system should behave in a way that most users will expect it to behave. The behavior should not *astonish* or *surprise* users. 

*Pareto principle*
80% of the effects come from 20% of the causes. 

*Convention over configuration*
Decrease number of decision that devs need to make, gaining simplicity but not necessarily losing flexibility. 
Devs only need to specify unconventional aspects of the application. 

For example if there's a class `Sale` in the model, the corresponding table in the database is called `sales` by default. Only if something deviates from this conventions something like `products_old` can be used. 

*Cyclic dependencies are evil*
Cause unwanted side effects. Creates tight coupling mutually dependent modules which reduces or makes impossible the separate re-use of a single module. 

Small local changes can spread into other modules.
Can result in infinite recursion or other unexpecte failures.
Difficult to test. 

Modifications in an upper-level layer should never lead to errors in deeper layers. 

*Favor Composition over Inheritance*
Composition is dynamic, inheritance static. 
Composition is flexible because behavior can be swapped at runtime. 
Inheritance breaks encapsulation. 
Used in the *Strategy Pattern, Adapter Pattern, Bridge Pattern, Decorator Pattern*

*Boy Scout Rule*
Leave every code you read in better shape than you found it. 

*Dependency Injection*
Target: Loose coupling.
Configuration and wiring with other components is taken out of the component. 

*Single Responsibility Principle (SRP)*
There should never be more than one reason for a class to change. 

*Advantages:* 
Reduction of complexity, increased readability, extensibility and maintenance, reusability and reduces errors, better testability. 

If we need to change a class that has more than responsibility the change might affect other functionality related to the other responsibility of the class.

*Open Closed Principle*
Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

*Cargo Cult Programming*
Ritual inclusion of code or program structures that server no real purpose. 

### Conway's Law
Organizations which design systems are constrained to produce deigns which are copies of the communication structures of these organizations. 

Based on the reasoning that in order for a software module to function, multiple authors must communicate frequently with each other. Therefor the software interface  of a system will reflect the social boundaries of the orga. 

Microservices reverse the logic of Conway's Law by structuring a system into independent, self-contained services, so that teams can work independently. 

## Law of Triviality
Parkinson's law. Organizations give disproportionate weight to trivial issues. 

## Postel's Law
Be conservative in what you send. Be liberal in what you accept.