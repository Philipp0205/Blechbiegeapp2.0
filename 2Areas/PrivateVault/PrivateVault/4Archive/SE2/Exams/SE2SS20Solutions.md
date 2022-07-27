## SS20 
[[Examination_SWE2_2020_SS_without_solution.pdf]]

### Exercise 1 
*a) Bounded Context* [[05DDDSummary]]
A Bounded Context is the boundary that surrounds a prticular model. This keeps the knowledge inside the boundary whilst ignoring noise from the outside world. 

*b)*
Context Mapping create a context maps which show how the dependencies and integration of Bounded Contexts.

*c)*
???

### Exercise 2 
*a) Production-efficiency* [[01PrinciplesSummary]]
Development time and the price of the software is an important aspect. The price is higher with inefficient production. High producition-efficiency means that software  can be developed further for years or even decades. 

*b) Global Util Helper*
The Single Responsibility Principle (SRP) is violated. There should never be more than one reason for a class to change. 
A global helper class increases complexity and readability. Also the extensibility and maintenance. Single parts are more difficult to reuse. 
If we need to change the global util helper that might affect other functionality because a lot of classes are using it. 

*c)*
The class violates the SRP. It has more than one responsibility and there could be more than on reason to change the class. 
It should be refactored in multiple classes. 

*Automobile* -> Tire, Engine, 



### Exercise 3 
![[SS20E3.png]]
*a)*
CCD = 27
ACD = 27 / 7 = 3.86

*c)*
CCD = 23
ACD = 23 / 8 = 2.88

*d)*
![[SS20E4d.png]]
!![[Pasted image 20210711151706.png]]

### Exercise 4 

![[SS20MetaModel.png]]

*c) Xtext Xtend*
Xtext is an open-source software framework for developing progrmmaing languages and DSLs.