# Composition vs. Inheritance: How to Choose? 

# Definition 
## Inheritance
A class may inherit the fields and method of its super class. 

Typical Use Case: Template Method Pattern. ([[Design Patterns]])

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
When a fields type is a class, the field will hold a reference to another object, thus creating an association relationship between them. 

Composition allows us to model objects that are made up of other objects. 
Defining a "has-a" relationship between them. 

For example, a Car is composed of different parts, including a engine. Ever car **has-a** Engine:

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

Source:
- https://www.thoughtworks.com/insights/blog/composition-vs-inheritance-how-choose
- https://www.baeldung.com/java-inheritance-composition

Refs:
Tags: type: #article topic: #programming #tech #oop