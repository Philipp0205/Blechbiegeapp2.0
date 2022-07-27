# Composition vs. Inheritance: How to Choose? 
Source:
- https://www.thoughtworks.com/insights/blog/composition-vs-inheritance-how-choose
- https://www.baeldung.com/java-inheritance-composition

Refs:
Tags: type: #article topic: #programming #tech #oop

---

# Definition 
## Inheritance
A class may inherhit the fields and method of its superclass. 

Typical UseCase: Template Method Pattern. ([[Design Patterns]])

```java
public class Parent {
	// variables
	// methods
}

public class Child extends Parent {
	// variables
	//methods
}
```

# Composition
When a Fields type is a class, the field will hold a refenerece to anothe robject, thus creating an association relationship between them. 

Composition allow us to model objects that are made up of other objects. 
Definining a "has-a" relationship between them. 

Foe example a Car is composed of different parts, inlcuding a engine. Ever car **has-a** Egnine:

```java
public class Engine {
	public String fuelType;
	
	public Engine() {
		//...
	}
	
	public String getFuelType() {
		//...
	}
	
	public String setFuelType() {
		//...
	}
}
```

```java
public class Car {
	public Engine engine;
 
	public Car(Engine engine) {
		this.engine = engine; 
	}
}
```