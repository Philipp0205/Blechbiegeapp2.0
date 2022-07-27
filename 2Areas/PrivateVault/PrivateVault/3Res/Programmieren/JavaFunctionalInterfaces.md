# Java functional Interfaces
[[!Resources]] [[java ]] [[programming]] [[!Porsche]]

---

## Key points
1. An interfaces containes one abstract interface
	- known as *functional Interface*
2. It can have any number of default, statric methods
3. A functional Interface can extend another interface only when it does not have any abstract method

**Predicates are combinable -> Vorteil **

## Examples of Custom Functional Interfaces
```java
@FunctionalInterface  
interface Sayable{  
    void say(String msg);   // abstract method   
}  
```

```java
public class FunctionalInterfacesExample {

    public static void main(String[] args) {

        Sayable sayable = (msg) -> {
            System.out.println(msg);
        };
        sayable.say("Say something ..");
    }
}
```

## Predefined-Functional Interfaces
- Java 8 provieds funcitonal interfaces to deal with functional programming by using lamda and method references

### Predicate
- Function that receives a generified value and returns a boolean. 
- Has a single method test that returns boolean value. 

### Function 
- Function that acceps one arugment and returns a reuislt

### Supplier 
- Reperensts a supplier of resutls

### Consumer 
- Represents an operation that adccepts a single arugment and returns no result.

### BiFunciton
- Represents a functions that adccepts two argumetn and returns a result

