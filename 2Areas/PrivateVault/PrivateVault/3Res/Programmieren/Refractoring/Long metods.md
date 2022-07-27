# Long methods
Refs: [[Refractoring Kurs]]
Tags: #refactorig

---
![[Pasted image 20201123143527.png]]
A method contains to many lines of code. 
Look afte methods that contain >10 loc. 

### Treatment
If you feel the need to comment on something inside a method, you should take this code and put it in a new method. 
Even a single line if it is necesary. 

#### Recipe 1: Extract Method
Move this code to a separate new method (or function) and replace the old code with a call to the method.

```java
void printOwing() {
  printBanner();

  // Print details.
  System.out.println("name: " + name);
  System.out.println("amount: " + getOutstanding());
}
```

```java
void printOwing() {
  printBanner();
  printDetails(getOutstanding());
}

void printDetails(double outstanding) {
  System.out.println("name: " + name);
  System.out.println("amount: " + outstanding);
}
```

#### Recipe 2: Reduce Local Variables and Parameters Before Extracting a Method
If local variables and parameters interfere with extracting a method, use Replace Temp with Query, Introduce Parameter Object or Preserve Whole Object.

**Replace Temp with Query**

```java
double calculateTotal() {
  double basePrice = quantity * itemPrice;
  if (basePrice > 1000) {
    return basePrice * 0.95;
  }
  else {
    return basePrice * 0.98;
  }
}
```

```java
double calculateTotal() {
  if (basePrice() > 1000) {
    return basePrice() * 0.95;
  }
  else {
    return basePrice() * 0.98;
  }
}
double basePrice() {
  return quantity * itemPrice;
}
```

**Introdice Parameter Obect**
![[IntrodouceParamterObject.png]]

**PreserveWhole Object**

You get several values from an object and then pass them as parameters to a method.
```java
int low = daysTempRange.getLow();
int high = daysTempRange.getHigh();
boolean withinPlan = plan.withinRange(low, high);
```
Instead pass whole object
```java
boolean withinPlan = plan.withinRange(daysTempRange);
```

#### Recipe 3: Relace Method with Method Object
If none of the previous recipes help, try moving the entire method to a separate object via Replace Method with Method Object.

You have a long method in which the local variables are so intertwined that you can't apply Extract Method.

```java
class Order {
  // ...
  public double price() {
    double primaryBasePrice;
    double secondaryBasePrice;
    double tertiaryBasePrice;
    // Perform long computation.
  }
}
```
Transform the method into a separate class so that the local variables become fields of the class. Then you can split the method into several methods within the same class.
```java
class Order {
  // ...
  public double price() {
    return new PriceCalculator(this).compute();
  }
}

class PriceCalculator {
  private double primaryBasePrice;
  private double secondaryBasePrice;
  private double tertiaryBasePrice;
  
  public PriceCalculator(Order order) {
    // Copy relevant information from the
    // order object.
  }
  
  public double compute() {
    // Perform long computation.
  }
}	
```

#### Recipe 4: Conditionals and Loops
Conditional operators and loops are a good clue that code can be moved to a separate method. For conditionals, use Decompose Conditional. If loops are in the way, try Extract Method.

You have a complex conditional (if-then/else or switch).
```java
if (date.before(SUMMER_START) || date.after(SUMMER_END)) {
  charge = quantity * winterRate + winterServiceCharge;
}
else {
  charge = quantity * summerRate;
}
```

Decompose the complicated parts of the conditional into separate methods: the condition, then and else.
```java
if (isSummer(date)) {
  charge = summerCharge(quantity);
}
else {
  charge = winterCharge(quantity);
}
```
