
## Architectural Principles 
- Value System
- Some principles 

## Build Management 
- Maven build lifecycle 
- Maven components 
- Difference Maven Gradle
- Ant stuff? 

## MDSD
[[03MDSDSummary]]
- GPLs vs DSLs
- Internal DSL / external DSL 
- 


## Architecture QA 
![[MeasureCoupling.png]]

### Martin Metrics
- Instability: I = Di / (Di + Do)
	- Di = incoming dependencies
	- Do = outgoing dependencies 
- Abstractness = Na / Nc
	- Nc: Total number of classes in a package 
	- Na: Number of abstract classes and interfaces in a package 
- Distance
	- D = A + I - 1 