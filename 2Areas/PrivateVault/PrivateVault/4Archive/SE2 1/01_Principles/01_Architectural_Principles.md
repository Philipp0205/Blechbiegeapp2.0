#lecture-notes 

[[SWE2-ArchitecturalPrinciples-new.pdf]]

---

# Value System
## Evolvability
## Correctness
## Productionefficiency
## Reflection

# Prolematic architectures - examples 
# Architecural principles
## Don't repeat yourself (DRY)
- Don't write the same piece of code in multiple places
- Applying DRY
	- Single source of truth
		- Model
	- Implements and maintian functionality only once
	
## YAGNI 
- You ain't gonna need it
- functionality that is implemented in advance is bad

## KISS
- Keep it short and simple 

## Principle of least astonishment

## Pareto principle 

## Conventions over configuration

## Cyclic dependencies are evil 

## Composition over Inheritance
- Compositiotn is dynamic, inheritance is static
[[Composition over Interitance]]

## Boy Scout Rule 
- Leave every code you read in better shape than you found it. 

## Dependency Injection
- Taget: Loose coupling
- Cinfuration and wiring with other components is traken out of the component 

## Global Util Helper is a bad idea... 
- No single resonsibility principle

## Single Responsibility Principle (SRP)
- There shuold never be more than one reason for a class to change.

## Open Closed Principle
- Software entities (classes, modules, functoins etc.) should be open for extension, but closed for modification.

##  Cargo Cult Programming
- Ritual inclusion of code or program structires that serve no real purpose
- Cargo cult software engineering: same phenomenon for the applicaton of Software Development Processes.

## Law of Triviality 
- Parkinson's law of traivialty, also known as bikeshedding. 
- Argument that organization give disproportionate weight to trivial issues. 

## Postel's Law 
- Be conservative in what you send. Be liberal in what you accept. 

[[01_Exercises]]