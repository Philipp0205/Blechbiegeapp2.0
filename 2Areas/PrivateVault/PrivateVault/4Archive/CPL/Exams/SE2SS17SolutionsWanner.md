[[Examination_SWE2_2017_SS_without_solution.pdf]]


## Exercise 1
*a) Different kinds of Continuous Integration*

*b) Steps of Ant custom Task*
1. Define task in build file 
`<taskdef name = "test" classname="testclass" />`
2. Use created task 
```xml
<target>
	...
	<test message="test" />
...
<target/>
```

*c) Gradle DSL*
The code parts defines that a specific dependency is needed in the project. 
The dependency is called "commoncs collections" and the version 3.2 is needed. 
For testing junir above version 4 is used. 

## Exercise 2
*a) YAGNI*
YAGNI means "you ain't gonna need it". It means that no functionality should implemented in advance because the dev thinks it might be used in the future. 
Costs time and money, will not be properly tested makes the code more complicated and there is a high chance that it never will be used. 

*b) Open Closed principle*
Software entities (classes, methods, modules) should be designed in a way that they are pen for extension but close for modification. 
That is because modification can always lead to unwanted side effects in other parts of the software. 

*c) Cargo Cult Programming*
CCP describes the ritual inclusion of code or software structures that server no real purpose. Often this is done by inexperienced devs who do not understand the code. 

## Exercise 3 
![[SS17E03.png]]

CCD = 27
ACD = 27 / 7 = 3.86

CCD = 26
ACD = 26 / 8 = 3.25

## Exercise 4
*a) MetaModel*
![[SS17MetaModel.png]]

*b) Advantages of a DSL compared to GPL [[03MDSDSummary]]*

*c) What is the Meta Meta Model in UML*

