## SS 19 
[[Examination_SWE2_2019_SS_without_solution.pdf]]

### Exercise 1
*a) Differences Maven build.xml and Build.gradle*
[[02BuildManagementSummary]]
Gradles *build.gradle* is a DSL and Mavens *build.xml* is a markup language. Gradles DSL is based on Groovy and was invetned to ditch the verbosity of XML and write more simple and clear statements. 

*b)*
```gradle
dependencies {
	compile-group: 'commons-collectoins', 
	name: 'commons-collections', 
	version: '3.2'
	
	testCompile group: 'junit',
	name: 'junit', 
	version: '4.+''

}
```

*c) Programming language for Plugins* 
Java should be used. 

*d) Gradle Build language*
Gradle provides a DSL for describing build. This build language is available in Groovy and Kotlin.

### Exercise 2
*a) Evolvability* [[01PrinciplesSummary]]
Software must have an internal structure that favors changes of the software. The simpler a software can be adapted, the higher its evolvability is. 
For the cost of a feature that does mean that it should be a fixed costs to implement it.

*b) Law of Triviality*
Means that companies give disproportionate weigh to trivial issues. 

*c) Boy Scout Rule* [[SWE2-ArchitecturalPrinciples-new.pdf]]
Leave every code you came across in better shape than you found it. 
Examples: 
- Renaming not self explanatory variables names 
- Split long method up into muliple methods 
- Remove unused code 
- Extract complex conditional into helper function.


### Exercise 3
![[SS19E03.png]]

*a)*
CDD = 27
ACD = 27 / 7 = 3.86

*c)*
CDD = 23
ACD = 23/8 = 2.86

*d)*
![[Pasted image 20210708144404.png]]

