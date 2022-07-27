## SS18 
[[Examination_SWE2_2018_SS_without_solution.pdf]]
[[SE2Fragen#SS18]]

### Excerise 1 
*a) Why Maven instead of Ant [[02BuildManagementSummary]]* 
Maven can do everything an does but add an abstraction. 
Maven solves weak points compared to Ant. 

*Plug-In-Concept* makes cross-project-reuse possible. 
Has *defined build lifecycle*, which Ant does not have. 
Uses *POM* for project description handling libraries. In ant invy is used for dependencies
Repo concept. Maven build up on own loavl repo and uses remote repos to load libs. 

*b) Gradle instead of Maven*
Gradle scales and therefore is better for big projects. 
Has many ways to manage dependencies. 
With DSL declarative builds and build by convention are possible. 

*c) Reasons to do CI in the cloud*
Integrating and building a large software system temporarily needs a huge amount of computer power. 
Huge costs, to achieve short integration time. 

*Solution*
Run CI in the cloud and only pay for computing power when needed. Tools that are used the CI chain can usually be chosen. 

### Exercise 2 
*a) Convention over Configuration [[01PrinciplesSummary]]*
Convention over config decreases that number of decision a Dev needs to make. Devs only specify unconventional aspects of the application. There more simple but not less flexibility. 

*b) Favor Composition over Inheritance*
Inheritance is static and composition is dynamic. 
With inheritance a structure of the software designed and later changes may not be implemented with that structure. With composition changes in the code can easily be included.

*c) Conway's law*
The law states that the communications structure in an orga are always represented in the software it creates. 

An example would be that in an hierarchical company the software might also be structure hierarchy. 
If one team create a software module and another team as well and these modules need to interact an interface is implemented similar to the communication of these two teams. 

A MS architecture reverses the logic of conways law by structuring a system into independent, self-contained services so that teams can work independently. 


### Exercise 3 

*a)*
![[Pasted image 20210708093741.png]]
CCD = 22
ACD = 22 / 7 = 3,13

---
*b) + c) [[SE2Fragen#SS18]]* 
![[SS18Solution.png]]
Three can be moved into other package because it is not used. 
Extract interface of G to resolve cycle. 
CCD = 20
ACD = 20 / 8 = 2,5

---
*d)*

![[Pasted image 20210708095024.png]]
The most instable class is the one with 0.75.

---

### Exercise 4
*a) Draw Metamodel*
![[4Archive/SE2/Exams/drawio/SS18MetaModel.png]]

*b) MDSD Terms [[03MDSDSummary]]*

*Platform independent model*

*Platform specific model*

*Meta Object Facility*

*Uml Profile*