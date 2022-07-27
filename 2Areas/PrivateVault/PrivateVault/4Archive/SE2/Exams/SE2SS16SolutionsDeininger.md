## Exercise 1 - Testing 
*What kind of test double is the class TestListener* 
Spy because it is recorder interactions an saves them in an ArrayList. 

*Characteristic*
Can use stubbing, which means that it provides output on calls.
Records interactions. 

*What to add for Mock*
configuration / verification of interaction.
A spy calls the real method on an object while a mock calls method on the double object. 

*Advantages*
Simple usage.

*Disadvantages*
LLearningnew framework
Having additional library 

*Other Testing tools*

Java-Reflection: Access or change private (or even constant fields) for test purposes .

Mockito: Mocking interfaces, simple creation of mock-objects, Injection of mock-objects in components under tests, 

Aspectj: Changing existing behavior, reaching otherwise unreachable code.

## Patterns 
![[SS16Pattern.png]]

```java
public interface Shape {
	public int count();
}

public class Circle {
	public int count () {
		return 1; 
	}
	
}

public class CompositeShape {
	private List<Shape> shapes = new ArrayList<Shape>();
	
	public void addShape(Shape shape) {
		shapes.add(shape);
	}
	
	public void removeShape(Shape shape) {
		// same thing.
	}
	
	public List<Shape> getShapes() {
		return shapes; 
	}
	
	public int count() {
		return shapes.size();
	}
}

```

[[SE2 - Design Patterns. Part 1.pdf]]
[[SE2 - Design Patterns. Part 2.pdf]]
*What is the role of design patterns for software maintenance?*
The main work does take place later in the maintencance. Applying the design pattern is only the initial step. 

*Risks of maintaining code not containing patterns?*
Not reusable. Hard to understand. 
Design patterns support low coupling and high cohesion and the open-closed principle. 
So not using them will result in close coupling, low cohesion and therefore in complex, difficult to reuse and not readable code.  

*Risks of overdoing patterns?*
Design patterns alone do not guarantee project success. 
Design patterns should not be used compulsively.
Do not integrate Design Patterns if they have no real puproes -> Cargo Cult Programming. 


## Exercise 3 
[[11MetricsSummary]]

*Afferent Coupling*
Indicator for the responsibility of the package. 

*Efferent Coupling*
Indicator for the independence of the package. 

*Afferent and Efferent Coupling*
![[SS16SolutionAfferentEfferentCoupling.png]]

*layered implementation?*
If it is a layered implementation the upper packages should have a less responsibility than the lower ones. This means that the CA should decrease from top to bottom. 
This is the case here. 

Lower packages should be more independent. that means that the CE should decrease from top to bottom. 
That is not totally the case but still fine because the numbers are the same and the lowest level is more independent. 

*Are these numbers sufficient?*
They are an indicator but they are not sufficient. To see if a class really need to be in a certain layer the code of that class need to be inspected.
Also it may be random that the numbers are right that does not mean that the architecture is layered correctly. 
